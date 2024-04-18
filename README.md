# VehicleClassification
Vehicle Image Classification based on Interior and Exterior Conditions of Vehicle using Azure Machine Learning and deploy it in an Azure Kubernetes Service (AKS) cluster. Here’s an updated architecture for this scenario:
Vehicle Image Classification for Interior and Exterior Conditions  - Architecture
1.	User Interface (UI):
o	The front-end where users interact.
o	Allows users to upload vehicle images for cleanliness assessment.
2.	Azure Blob Storage:
o	Stores the uploaded vehicle images.
o	Triggers an event in Azure Event Grid upon image upload.
3.	Azure Event Grid:
o	Listens for image upload events from Blob Storage.
o	Notifies Azure Functions to process the newly uploaded image.
4.	Azure Functions:
o	Receives the image URL from Event Grid.
o	Calls the Azure Computer Vision API to analyze image cleanliness.
o	Persists the API response in Azure Cosmos DB along with image metadata.
5.	Azure Computer Vision API:
o	Part of Cognitive Services.
o	Analyzes vehicle images to determine cleanliness.
o	Returns classification results (e.g., “clean,” “dirty,” “damaged”).
6.	Azure Cosmos DB:
o	Stores metadata about each image, including cleanliness classification.
o	Enables querying and reporting on image cleanliness data.
7.	AKS Cluster:
o	Backed by GPU-enabled virtual machines (VMs).
o	Hosts the machine learning model for image classification.
o	Scales horizontally for high-scale production deployments.
8.	Machine Learning Model:
o	Trained using labeled vehicle images.
o	Deployed as a web service on AKS.
o	Receives image URLs and predicts cleanliness.
9.	Web or Mobile Front End:
o	Consumes cleanliness classification results.
o	Displays cleanliness status to users.
10.	Alternatives:
o	Custom Vision Service: For building custom image classifiers.
o	Cognitive Search: For querying metadata and finding specific images.
o	Logic Apps: If real-time processing isn’t required.
Remember that this approach retrieves the results of the classification but not the uploaded image itself. By leveraging Azure services, we can efficiently process vehicle images and enhance cleanliness assessment for better decision-making1.
