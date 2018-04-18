# S3-ansible-playbook-bundle
GlusterFS S3 ansible playbook bundle(APB)


oc cluster up --public-hostname=10.70.42.192  --service-catalog=true 

ROUTING_SUFFIX="10.70.42.192.nip.io"

TEMPLATE_URL=${TEMPLATE_URL:-"https://raw.githubusercontent.com/openshift/ansible-service-broker/master/templates/deploy-ansible-service-broker.template.yaml"}

DOCKERHUB_ORG=${DOCKERHUB_ORG:-"ansibleplaybookbundle"} # DocherHub org where APBs can be found, default 'ansibleplaybookbundle'

ENABLE_BASIC_AUTH="false"

VARS="-p BROKER_CA_CERT=$(oc get secret -n kube-service-catalog -o go-template='{{ range .items }}{{ if eq .type "kubernetes.io/service-account-token" }}{{ index .data "service-ca.crt" }}{{end}}{{"\n"}}{{end}}' | tail -n 1)"

curl -s $TEMPLATE_URL   | oc process   -n ansible-service-broker   -p DOCKERHUB_ORG="$DOCKERHUB_ORG"   -p ENABLE_BASIC_AUTH="$ENABLE_BASIC_AUTH"   -p NAMESPACE=ansible-service-broker   -p ROUTING_SUFFIX="$ROUTING_SUFFIX"   $VARS -f - | oc create -f -

oc adm policy add-cluster-role-to-user cluster-admin developer
oc login -u developer'

