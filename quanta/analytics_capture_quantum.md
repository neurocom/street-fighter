# Analytics Capture Quantum
The analytics capture capability is responsible for monitoring the application's usage, gathering information regarding all trip events and combining this information with third party analytics sources that are available as well as gathering baselines regarding industry trends. Using the Analytics Capture, we can  
- Provide the "end-of-year" summary report to the Road Warriors.
- Compare the adoption of the service by teservation type and destination compared to industry baselines.
- Create dashboards on total system usage per use case  
- Create datamarts with the users preferences per resevation type, airline, rental company etc.
In the future, we should use the Analytics Capture data as a platform for providing insights to companies working in the travel sector. Another possible commercial use is using the affiliate programs of specific vendors when users are sharing their trips to others or via social media   

The following diagram describes the architecture for the Analytics Capture in detail.
<p align="center">
<img width="1000" src="../assets/analytics.png">
</p>

## Components

### (De)Anonymizer
- The (De)Anonymizer reads events from the main architecture broker that provide information origination from road warriors.  
- It is used as an in-between (Anoymizer) to ensure that the analytics database does not hold information directly linked to users. This is needed to ensure GDPR Compliance and encance security.
- The Reporting Service API can use the DeAnonymizer to produce the "end-of-year" summary reports 

### Collector
- The collector component is responsible for periodically gathering information from external sources. The collector schedules the information retrieval accordingly, depending on the source and


### OLAP DB
- All Analytics information is persisted on a database that is capable of handling analytic workloads. The database engine is directly used by the Reporting Services and the ETL/ELT service. 
- All information within the OLAP DB is anonymized, to ensure GDPR compliance and information security.

### Reporting Sevice API
- We use two instances of Reporing Services. The first instance is for all reports that need user information and has access to the DeAnonymizer. The second instance may be used by external users in the future to provide information regarding trends, frequent locations, user preferences etc.

### ETL/ELT
- This service is used for all transformations that need to take place within the OLAP DB
- Transformation examples include: Facts, Dimensions, Datamarts, Aggregations, Explorations
- The ETL/ELT component is a client that schedules and sends jobs for the OLAP DB to execute via SQL based on workflow 

## Communications Between Components
Traffic events and reservation events are loaded asynchronously to the OLAP DB database. Information from external sources is smaller in volume, updated less frequently and is loaded synchronously. All report requests are retrieved synchronously by the reporting services.

## Related ADRs
- [ADR12 Analytics OLAP](../adrs/analytics.md)
- [ADR13 GDPR](../adrs/gdpr.md)

