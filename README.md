# ci-cd-solution
## Setup
$ minishift start
$ minishift oc-env
$ eval $(minishift oc-env)
$ oc login
## Create Projects
$ oc new-project cicd --display-name="CI/CD"
$ oc new-project app-dev --display-name="App DEV"
$ oc new-project app-stage --display-name="App STAGE"
$ oc get projects
# Grant Jenkins Access to Projects
$ oc policy add-role-to-user edit system:serviceaccount:cicd:jenkins -n app-dev
$ oc policy add-role-to-user edit system:serviceaccount:cicd:jenkins -n app-stage
$ oc new-app -n cicd -f cicd-template.yaml