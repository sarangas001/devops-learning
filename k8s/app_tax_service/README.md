## MICRO SERVICE APLLICATION DEPLOY

# STEPS

1. Some service are only interly access and other's are need to be acces through the internet.
2. In this example, service-a is a access through the internet and the sevice-b is the internal access.
2. We need to change the names, port env and the service spec type 


# THEORY

1. Service component internal access called ClusterIP. This is giving only internal access. Also it can access <service-name>:<port>
2. Other one is Normal one

# SERVICE - B
apiVersion: v1
kind: Service
metadata:
  name: service-b
spec:
  selector:
    app: service-b
  type: ClusterIP
  ports:
    -  port: 4000
       targetPort: 4000

# SERVICE - A

apiVersion: v1
kind: Service
metadata:
  name: service-a
spec:
  selector:
    app: service-a
  type: NodePort
  ports:
    -  port: 3000
       targetPort: 3000
       nodePort: 32000

