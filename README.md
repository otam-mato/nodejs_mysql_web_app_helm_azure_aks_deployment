# Node.JS + MySQL Web App.<br><br>HELM deployment and upgrading the app on a Kubernetes cluster launched on MS Azure AKS.

<p align="center">
  <a href="https://skillicons.dev">
    <img height="50" width="50" src="https://cdn.simpleicons.org/helm/blue" /><img src="https://skillicons.dev/icons?i=kubernetes,azure,docker,nodejs,mysql"/>
  </a>
</p>



<br>

> [!NOTE]
> This is a part of a series of demo projects in which I manipulate a Node.js application using various technologies.<br>
>
> The app built using Node.js and Express and integrates with MySQL database, originally presented at this [GitHub Repository](https://github.com/otam-mato/nodejs_mysql_web_app_terraform.git). The previous [project](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes.git) involved the "Canary" deployment on **AWS EKS**.
>
> In the current installment, we're deploying the web application on **MS Azure AKS** using **HELM**. Subsequently, we'll introduce the second version of the app and then rollback to the first version with HELM.
<br>

## Deployment Strategy

The **HELM** is a package manager for Kubernetes applications. It simplifies the deployment and management of applications on Kubernetes clusters. Helm uses charts, which are packages of pre-configured Kubernetes resources, to define, install, and upgrade even the most complex Kubernetes applications and their dependencies. It helps streamline the deployment process, reduce errors, and enable versioning and rollbacks for Kubernetes applications.

1. In this demo, we will use **HELM** to deploy:
   - V1 deployment which will host the version 1 of the app.
   - V2 deployment which will host the version 2 of the app.
   - Finally we will rollback V2 to V1.

   V1 and V2 versions uploaded into this [DockerHub repository](https://hub.docker.com/repository/docker/montcarotte/fullstack_nodejs_mysql_demo/general)

2. The app and its database are placed in separate Kubernetes pods to secure decoupling, resource isolation, scaling and resilience.

<br>

## Technologies used
- **MS Azure**
- **AKS (Azure Kubernetes Service)**
- **Node.JS**
- **Express**
- **JavaScript**
- **MySQL**
- **Docker**
- **Kubernetes**
- **HELM**
<br>

## Application Functionality

This web application interfaces with a MySQL database, facilitating CRUD (Create, Read, Update, Delete) operations on the database records.

**<details markdown=1><summary markdown="span">Detailed app description</summary>**

## Summary

The app sets up a web server for a supplier management system. It allows viewing, adding, updating, and deleting suppliers. 

#### **Dependencies and Modules**:
   - **express**: The framework that allows us to set up and run a web server.
   - **body-parser**: A tool that lets the server read and understand data sent in requests.
   - **cors**: Ensures the server can communicate with different web addresses or domains.
   - **mustache-express**: A template engine, letting the server display dynamic web pages using the Mustache format.
   - **serve-favicon**: Provides the small icon seen on browser tabs for the website.
   - **Custom Modules**: 
     - `supplier.controller`: Handles the logic for managing suppliers like fetching, adding, or updating their details.
     - `config.js`: Keeps the server's settings for connectind to the MySQL database.

#### **Configuration**:
   - The server starts on a port taken from a setting (like an environment variable) or uses `3000` as a default.

#### **Middleware**:
   - It's equipped to understand data in JSON format or when it's URL-encoded.
   - It can chat with web pages hosted elsewhere, thanks to CORS.
   - Mustache is the chosen format for web pages, with templates stored in a folder named `views`.
   - There's a public storage (`public`) for things like images or stylesheets, accessible by anyone visiting the site.
   - The site's tiny browser tab icon is fetched using `serve-favicon`.

#### **Routes (Webpage Endpoints)**:
   - **Home**: `GET /`: Serves the home page.
   - **Supplier Operations**: 
     - `GET /suppliers/`: Fetches and displays all suppliers.
     - `GET /supplier-add`: Serves a page to add a new supplier.
     - `POST /supplier-add`: Receives data to add a new supplier.
     - `GET /supplier-update/:id`: Serves a page to update details of a supplier using its ID.
     - `POST /supplier-update`: Receives updated data of a supplier.
     - `POST /supplier-remove/:id`: Removes a supplier using its ID.

#### **Starting Up**:
   - The server comes to life, starts listening for visits, and announces its awakening with a log message.

</details>

<br>

## Implementation Steps

Follow these steps for successful implementation:

1. [**Create infrastructure for your cluster**](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes/blob/main/README.md#prerequisites)
2. [**Create an AKS cluster**](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes/blob/main/README.md#prerequisites)
3. [**Create an Azure VM**]()
4. [**Connect the Azure VM to AKS cluster**]()
5. [**Install HELM**]()
6. [**Create a HELM chart**]()
7. [**Deploy the V1 app**](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes/blob/main/README.md#1-create-the-deployment-of-v1-of-the-app)
8. [**Upgrade the app to V2**](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes/blob/main/README.md#4-create-the-deployment-of-v2-of-the-app)
9. [**Roll the V2 back to V1**](https://github.com/otam-mato/nodejs_mysql_web_app_kubernetes/blob/main/README.md#7-test-the-app)

<br>

<img width="915" alt="Screenshot 2023-12-27 at 17 21 54" src="https://github.com/otam-mato/nodejs_mysql_web_app_HELM_AZURE_AKS_deployment/assets/113034133/51ee6462-a454-45bc-ad73-5d429b36dbe0">
