# RHOAR Vertex Hello World
Vertex Hello World Microservice - RHOAR course

## Compile Application
```
mvn clean package
```

## Openshift Deployment
```
export HELLO_PROJECT_NAME=helloworld-http
oc new-project $HELLO_PROJECT_NAME
mvn clean fabric8:deploy -Popenshift
```

### Deployment Test
```
export HELLO_URL=http://$(oc get route hello-microservice -n $HELLO_PROJECT_NAME -o template --template='{{.spec.host}}')
curl -X GET "${HELLO_URL}/John"
```
