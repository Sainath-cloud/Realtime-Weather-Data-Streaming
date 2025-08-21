# ☁️ Real-Time Weather Report Project

This project implements an end-to-end real-time streaming data engineering pipeline designed to collect, process, and visualize real-time weather data. It's built to provide continuous weather updates and enable real-time alerting for extreme weather conditions.

-----

## 🏗️ Project Architecture

The system is designed to ingest data from an **Event Hub**, process it through **Azure Functions** and **Databricks**, store and transform it within **Microsoft Fabric**, and finally visualize it in **Power BI** for real-time reporting. **Azure Data Activator** is used for alerting on specific weather conditions.

  * **Event Hub**: Acts as the ingestion point for raw weather data streams.
  * **Azure Function App**: Used for serverless data ingestion and potential preliminary processing before sending data to subsequent stages.
  * **Databricks Notebooks**: Utilized for more complex data transformations, aggregations, and potentially machine learning tasks on the streamed data.
  * **Microsoft Fabric**: The central analytics platform for data processing (e.g., Lakehouse, Data Pipelines) and storage (KQL Database, Eventhouse).
  * **Azure Data Activator**: Configured within Fabric to monitor processed data for specific weather thresholds and trigger alerts (e.g., email notifications for extreme weather).
  * **Power BI Desktop Report**: Connects to the processed data in Fabric to create interactive, real-time dashboards for weather monitoring.

-----

## 🛠️ Components & Technologies

This project leverages various Microsoft Azure and Fabric services:

  * **Azure Event Hubs**: Scalable real-time data ingestion service.
  * **Azure Functions**: Serverless compute for event-driven processing.
  * **Azure Databricks**: Unified analytics platform for data engineering and data science.
  * **Microsoft Fabric**:
      * **Eventstream**: For real-time data streaming within Fabric.
      * **Eventhouse**: A powerful database for high-volume, real-time data.
      * **KQL Database / Queryset**: For querying and analyzing real-time data.
      * **Data Activator**: For real-time monitoring and alerting.
      * **Semantic models**: Underlying data models for Power BI.
  * **Power BI Desktop**: For creating interactive data visualizations and reports.
  * **Git / GitHub**: For version control and collaborative development of code artifacts.

-----

## 📁 Local Project Structure

This repository is organized to contain the key code artifacts and documentation for the project:

```
my-data-project/
├── databricks/
│   └── weather_notebook.ipynb      # Databricks notebook for data processing
├── function_app/
│   ├── .vscode/                    # VS Code settings for Function App
│   ├── your_function_app_code.py   # Python code for Azure Function
│   └── host.json                   # Function App configuration
├── docs/
│   └── fabric_flowchart.png        # Architecture diagram of the Fabric flow
├── powerbi/
│   └── weather_report.pbix         # Power BI Desktop report file
├── README.md                       # This readme file
└── .gitignore                      # Files/folders to ignore in Git
```

-----

## 🚀 Setup & Deployment

Setting up this project involves deploying resources across Azure and configuring items within Microsoft Fabric. This section provides a high-level overview. For detailed deployment steps, please refer to the specific documentation or video tutorial where this project originated.

1.  **Azure Resource Deployment**:

      * Deploy an **Azure Event Hub** instance.
      * Set up an **Azure Function App** and deploy the `function_app` code. Configure it to send data to the Event Hub.
      * Configure **Azure Databricks** workspace and import the `databricks/weather_notebook.ipynb` to run your data processing logic, potentially pulling data from or pushing data to Event Hub/Fabric.

2.  **Microsoft Fabric Configuration**:

      * Create a **Microsoft Fabric workspace** and ensure it's assigned to a premium capacity (e.g., Trial capacity).
      * Set up an **Eventstream** to consume data from your Azure Event Hub.
      * Create an **Eventhouse** or **KQL Database** to store and query your processed streaming data.
      * Define **KQL Querysets** for specific data views.
      * Configure **Data Activator** to define alerts based on conditions in your Eventhouse/KQL data.
      * Develop **Semantic models** in Fabric based on your Eventhouse/KQL data for Power BI consumption.

3.  **Power BI Report Setup**:

      * Open `powerbi/weather_report.pbix` with Power BI Desktop.
      * Ensure the data source connections point to your Fabric Semantic model. Refresh the report to pull live data.

-----

## 📊 Usage

Once deployed and configured, the system will continuously:

  * Ingest real-time weather data into Event Hub.
  * Process and transform this data through Azure Functions and Databricks.
  * Store and prepare the data within Microsoft Fabric.
  * Update the Power BI report with the latest weather information.
  * Trigger automated alerts via Data Activator if predefined extreme weather conditions are met.

This project provides a robust framework for real-time data analytics and operational intelligence.
