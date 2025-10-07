The framework has been updated to run from Hydra-based configurations.

- All the configurations are fully composable - where the common
  configurations reside in `commons/hydra/training` folder

- Specific configurations reside in `hydra-configs`

- The entry point of the configuration is an instance of the
  `TrainerPipelineConfig` pydantic model.

- The pipeline is run by giving an entry point configuration as an
  argument, for eg `ranker_torch` -

  - `python main_training.py -cn ranker_torch -r`

  - There should be a corresponding yaml file for entry point i.e.
    `hydra-configs/ranker_torch.yaml`

- All configuration classes are pydantic models.

- Most configuration classes follow plugin architecture, which means one
  can define their implementation of config, and it would be
  automatically registered and instantiated depending on the
  configuration. More specifically, `training_strategy` and `model` are
  pluggable with all the necessary glue code to support their
  pluggability.

- While different implementations of `training_strategy` are part of
  `commons`, for `model` only the base `ModelConfig` is defined in
  commons, and concrete implementation of model-specific config is left
  to use case. For example,
  `mtl_ranker/mtl_pytorch/train/ranking_model_config.py` defines ranking
  model-specific `TorchRankingModelConfig`. The only requirement is that
  this model class should be imported in `main_training.py,` (such a
  check is not necessary, though for safe guards and ensuring I use
  imported ModelConfig I had put this) -

  - if isinstance(pipeline_cfg.model, TorchRankingModelConfig):
    model_builder = pipeline_cfg.model.get_builder(stats) else: raise
    ValueError(f\"Unknown model: {pipeline_cfg.model}\")

- Feature configurations are in `feature_configs.py` - all the common
  data transformations are automatically generated with feature
  configs - so there is no common data preprocessing in
  `feature_utils.py`

- The best use of feature configs is left to the model implementation.
  One can write a fully hardcoded model or make it configurable using
  feature configurations. My understanding is feature configurations
  would evolve more as new models are implemented. As models are built
  using feature configurations, they can also be part of the commons
  framework. For example, with a bit of refactoring of the retrieval
  model - the same model code can be used for both user\<\>item and
  user\<\>creator two towers.

**Notable changes**

- All methods of TrainerPipeline and its subclasses now receive
  TrainerPipelineConfig as arguments - this way entire pipeline
  configuration is available to various methods. Adding new configs or
  changes in existing configs would only require changes in the
  corresponding pedantic configurations and their use in the
  corresponding method - method argument changes may not be required.

- `train` method of TrainingStrategy and its subclasses also receive
  TrainerPipelineConfig - so it also has a full view of configuration,
  rather than train specific.

- mlfow and wandadb integrations are also pluggable via trackers config.
  Enable/disable, or configuration changes can be done externally in
  hydra configurations, and any implementation changes would be limited
  to `trackers_config.py`. New experiment-tracking frameworks can be
  integrated, or existing ones can be changed without impacting any
  other code.

- eval_worker also does not assume any hardcoded field names - it has
  been refactored in configurations.

**Why pydantic**

- pydtantic models are more powerful than data classes.

- pydantic models support pluggability - see `__init__` method of
  TrainerPipelineConfig and corresponding glue code in
  `TrainingStrategyConfig`/`__init_subclass__`

- We can add a lot of data validators at configuration time and remove
  those checks from various other places.

- With custom glue between hydra and pydantic - we get actual instances
  of classes rather than DictConfig of OmegaConf, if we were using plain
  vanilla Hydra.
