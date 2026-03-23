## Storage Systems

The system uses different storage solutions based on the type of data and how it is used. For structured and transactional data like patient records and hospital operations, a relational database (such as MySQL) is used. This ensures data consistency and supports frequent updates.
For real time ICU data, a streaming system like Kafka is used to capture continuous data from devices. This data is then stored in a Data Lake, which holds all types of data (structured, semi-structured, and unstructured) in raw format. The Data Lake provides flexibility and scalability for large volumes of incoming data.
On top of the Data Lake, a Data Lakehouse is used to organize and process the data into a structured format for analytics. This allows efficient querying for reports and dashboards. A feature engineering layer is also included to prepare data for machine learning models, such as predicting patient readmission risk.
Additionally, a vector database is used to support natural language queries from doctors. It helps in understanding the meaning of queries and retrieving relevant patient information more accurately.

## OLTP vs OLAP Boundary

The OLTP (Online Transaction Processing) layer includes the hospital’s operational database, where real-time transactions such as patient admissions, updates, and treatments are recorded. This layer is optimized for fast and reliable operations.
The OLAP (Online Analytical Processing) layer starts when data is moved into the Data Lake and then processed into the Data Lakehouse. This layer is used for analytics, reporting, and machine learning. It handles large volumes of historical and real-time data without affecting the performance of the OLTP system.
By separating OLTP and OLAP, the system ensures that daily operations remain efficient while still enabling advanced analytics and insights.

## Trade-offs

One major trade-off in this design is the increased complexity due to multiple systems such as the Data Lake, Lakehouse, streaming pipelines, and vector database. While this improves scalability and flexibility, it also requires more effort to manage and maintain.
This can be handled by using workflow orchestration tools like Airflow and ensuring proper data validation at each stage. Another trade-off is potential delay in analytics due to batch processing. However, this is reduced by using streaming pipelines for real-time data, especially for ICU monitoring and alerts.
Overall, the design balances performance, scalability, and real-time capabilities effectively.
