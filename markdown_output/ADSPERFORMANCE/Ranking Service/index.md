## Ranking Service

1.  Responsible for running the runtime ranking service to order given
    list of campaigns per adrequest by predictions from models.

2.  Repo:
    <https://gitlab.dailyhunt.in/nh-ads-platform/RustRealTimePredictAPI>

3.  Tech: Rust, gRPC, Kafka

4.  Rough Responsibility :

    1.  PredictionService: Submodule to generate predictions from a
        given model

    2.  RankingService: Process request, call prediction, post process
        predictions, generate scores, sort and return.

    3.  Rust Trees: Conversions of the Xgboost models to Rust code.

    4.  Cache: Maintain, refresh and validate runtime in memory cache.
