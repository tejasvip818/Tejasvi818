gcloud config set project qwiklabs-gcp-04-55676305fb94

export PATH=$PATH:"/home/${USER}/.local/bin"

cd ~/adk_eval_challenge_lab

uv init

uv add -r requirements.txt

source .venv/bin/activate

terraform init

cat << EOF > bigquery_agent/.env
GOOGLE_GENAI_USE_VERTEXAI=TRUE
GOOGLE_CLOUD_PROJECT=qwiklabs-gcp-04-55676305fb94
GOOGLE_CLOUD_LOCATION=global
MODEL=gemini-3.5-flash
EOF
