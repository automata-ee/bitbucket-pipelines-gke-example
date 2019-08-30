# bitbucket-pipelines-gke-example
Instructions to get Bitbucket Pipelines working with Google Cloud Kubernetes Engine.

I got this working after a bit of testing and copying examples from various 
sites.  I wish I could reference each source but I can't remember from where 
I got each piece. 

# What does it do?
It builds an image from a Dockerfile stored at the root of the git repo, sends
the image to Google Cloud Registry and update one deployment (in this example 
an app named api) container with the freshly built image.

You need to create a service account with the appropriate permissions. Export 
the key as json format and conver the contents to base64. Go to the pipelines
settings and create the $GCLOUD_(DEV|PRD)_API_KEYFILE secrets with the encoded 
information.

As you have probably notice this particular example uses different projects and
clusters for production and development.

The following variables are used:

* GCLOUD_DEV_PROJECT: development project ID (not name)
* GCLOUD_PRD_PROJECT: production project ID (not name)
* GCLOUD_DEV_API_KEYFILE: development service account base64 encoded key stored as secret
* GCLOUD_PRD_API_KEYFILE: production service account based64 encoded key stored as secret
* GCLOUDNAMESPACE: kubernetes namespace
* GCLOUD_DEV_ZONE: development compute zone
* GCLOUD_PRD_ZONE: development compute zone


Have a lot of fun. :)
