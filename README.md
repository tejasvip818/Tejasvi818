gcloud storage cp -r gs://qwiklabs-gcp-03-789e946ed1a3-bucket/adk_eval_challenge_lab .

gcloud config set project qwiklabs-gcp-03-789e946ed1a3

export PATH=$PATH:"/home/${USER}/.local/bin"

cd ~/adk_eval_challenge_lab

uv init

uv add -r requirements.txt

source .venv/bin/activate

terraform init
