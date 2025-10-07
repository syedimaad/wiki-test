repo link: <https://gitlab.dailyhunt.in/ai-lab/audio_fingerprinting>

VM: 10.10.38.158 (flask api and mongodb, both running on this system)

How it works:

- Query: (works, in production)

  - audio_ids are received corresponding which audio es
    ([[https://josh-audios-es-gke.myjosh.in:9200/]{.underline}](https://josh-audios-es-gke.myjosh.in:9200/))
    is queried and an the audio is loaded

  - the loaded audio is broken up into fingerprints

  - these fingerprints are used to query a mongodb collection containing
    all fingerprints of copyright audios in Josh.

  - the top matched audio is returned

- Ingestion (Doesn't work, in production)

  - new audio ids are read from an sqs queue

  - fingerprints are generated for this audio

  - pushed to mongo,

Current state:

- The current number of songs in the index is approx : 300k

- Ingestion hasn't worked since: July 2022

- ingestion doesn't work due to scaling issue, to fix this audio
  fingerprinting v2 was developed but was not deployed into production.
