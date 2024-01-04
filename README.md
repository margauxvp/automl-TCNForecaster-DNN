![image](https://github.com/margauxvp/automl-TCNForecaster-DNN/assets/33750077/60b23eb8-9b25-4114-a00f-dc0ba8e3b544)

**Advice on Endpoints**
After you train machine learning models or pipelines, you need to deploy them to production so that others can use them for inference. Inference is the process of applying new input data to the machine learning model or pipeline to generate outputs. While these outputs are typically referred to as "predictions," inferencing can be used to generate outputs for other machine learning tasks, such as classification and clustering. In Azure Machine Learning, you perform inferencing by using endpoints and deployments. Endpoints and deployments allow you to decouple the interface of your production workload from the implementation that serves it.

Endpoint: 
Suppose you're working on an application that predicts the type and color of a car, given its photo. For this application, a user with certain credentials makes an HTTP request to a URL and provides a picture of a car as part of the request. In return, the user gets a response that includes the type and color of the car as string values. In this scenario, the URL serves as an endpoint.

An endpoint is a stable and durable URL that can be used to request or invoke a model. You provide the required inputs to the endpoint and get the outputs back. An endpoint provides:
a stable and durable URL (like endpoint-name.region.inference.ml.azure.com),
an authentication mechanism, and
an authorization mechanism.

Azure Machine Learning allows you to implement online endpoints and batch endpoints. Online endpoints are designed for real-time inference—when you invoke the endpoint, the results are returned in the endpoint's response. Batch endpoints, on the other hand, are designed for long-running batch inference. Each time you invoke a batch endpoint you generate a batch job that performs the actual work.

Deployment:
Furthermore, say that a data scientist, Alice, is working on implementing the application. Alice knows a lot about TensorFlow and decides to implement the model using a Keras sequential classifier with a RestNet architecture from the TensorFlow Hub. After testing the model, Alice is happy with its results and decides to use the model to solve the car prediction problem. The model is large in size and requires 8 GB of memory with 4 cores to run. In this scenario, Alice's model and the resources, such as the code and the compute, that are required to run the model make up a deployment under the endpoint.
you can also create multiple deployments under one endpoint (e.g. if another compute with gpu for instance  or code is needed)

A deployment is a set of resources and computes required for hosting the model or component that does the actual inferencing. A single endpoint can contain multiple deployments. These deployments can host independent assets and consume different resources based on the needs of the assets. Endpoints have a routing mechanism that can direct requests to specific deployments in the endpoint.

To function properly, each endpoint must have at least one deployment. Endpoints and deployments are independent Azure Resource Manager resources that appear in the Azure portal.


**More info:**
Find all code (scoring script, conda env, model.pt via automl or jobs -> display name -> child jobs -> click through -> best trial / trials and choose one -> output + logs. You don’t find this when you registered it in in the models. Sad. Unless if you go to your model and then job id

The scoring script is only for online endpoints. We will use the scoring script from the github ml examples but the conda environment from both the github (for the image) and from this  model the yml file (but delete all the dependencie numbers for the last ones). Build environment like this and then you can fixate once built in the batch deployment, no need to continuously rebuild. 
![image](https://github.com/margauxvp/automl-TCNForecaster-DNN/assets/33750077/2a9f21cc-07b4-4fd0-ba64-b3c24e45ba49)
