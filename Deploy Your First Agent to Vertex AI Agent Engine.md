### Deploy Your First Agent to Vertex AI Agent Engine

- To deploy we need two things :
  1. Google Agent Development Kit(ADK)
  2. Vertex AI Agent Engine

### 5 Steps to Deploy ADK Agents To Agent Engine

**Step 1 :** Create Agent with ADK
**Step 2 :** Create our project in GCP
**Step 3 :** Setup AI resources (Vertex AI)
**Step 4 :** Setup Google Cloud CLI (Run locally)
**Step 5 :** Deploy Agent to the Cloud

**Step 3:**
-> After creating a new project in Google cloud copy the project id and paste it 
in the .env file the below details

1. GOOGLE_CLOUD_PROJECT
2. GOOGLE_CLOUD_LOCATION
3. GOOGLE_CLOUD_STAGING_BUCKET

**Step 4 :**

Go to the below two links and perform those steps

https://google.github.io/adk-docs/get-started/quickstart/
https://cloud.google.com/sdk/docs/install

> gcloud auth login
> gcloud init
Enter your choice : 1
Enter your choice : 1
Please enter project 1

> adk web

**Step 5 :** Deploy Agent to the Cloud 

#First wrap the agent in ADkApp

app = reasoning_engines.AdkApp(
  agent = root_agent,
  enable_tracing = True
)

#Now deploy to Agent Engine

remote_app = agent_engine.create(
  agent_engine = app,
  requirements = [
    "google-cloud-aiplatform[adk,agent_engines]"
  ],
  extra_packages = ["./adk_short_bot"],
)
)

#Run the below command

> poetry run deploy-remote --create





