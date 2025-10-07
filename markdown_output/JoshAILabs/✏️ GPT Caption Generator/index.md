Prod url - <https://prod-gpt-api.myjosh.in/>

Repo -
<https://gitlab.dailyhunt.in/josh-ai-labs/gpt-post-sugestions/-/tree/prod?ref_type=heads>

Monitoring -
<https://verse.in.sumologic.com/ui/#/dashboardv2/KKjFwRFTTMV95eC7KQdfUVviMUSI5L1xPfGpkZGAIhqt6rBPhOIq4ADhJG27>

Deployment - Kubernetes, using docker images -
`joshprodregistry.azurecr.io/gpt-api:latest`

## Description

This program will generate captions for the posts based on the frames in
the video.

**Input** :

3-5 images from the videos uploaded by creator

*Input request format*

{ \"images\": \[ \"string\" \], \"num_posts\": 5,
\"num_words_per_post\": 20 }

**Output** :

n number of captions from gpt model ( da-vinci - 003)

## Flow

**Config file**

config.json → This holds gpt api config and prompt template

**Main func**

app_api.py

- Program will receive the request at
  <https://prod-gpt-api.myjosh.in/suggestions>

- `vis_processors` ← this function extracts the captions, based on the
  BLIP 2 model. Input to the function is the images from the client.

- `get_prompt` ← This will generate the prompt based on the inputs

- `get_completion` ← This helper function send api request to gpt
  endpoint and gets result

- Finally the result is sent to back to client

**Deployment**

Docker file is created using this → Dockerfile .

Finally CICD set up is configured here → .gitlab-ci.yml (Just need to
push the code to dev branch)
