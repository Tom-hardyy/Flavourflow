# FlavourFlow — Food Delivery Data Warehouse
A purpose-built data warehouse system for food-delivery analytics.
Integrates public delivery datasets via Python-based ETL into a
star-schema SQL Server database, with Power BI reporting.
## Stack
- Orchestration: Apache Airflow
- Processing: Python 3.10+, Pandas, SQLAlchemy, PyODBC
- Database: Microsoft SQL Server
- Reporting: Power BI
## Setup
1. Clone the repo
   git clone [github.com](https://github.com/)[your-username]/flavourflow.git
2. Install dependencies
   pip install -r requirements.txt
3. Configure environment
   cp .env.example .env
   # Fill in DB credentials and file paths
4. Initialise Airflow
   airflow db init
   airflow users create --username admin --role Admin \
     --email admin@example.com --firstname Thomas --lastname Hardy
5. Place DAGs
   Copy airflow/dags/* to your Airflow DAGs folder
6. Run SQL setup
   Execute sql/ddl/ scripts in order (01 → 04) against your SQL Server
7. Trigger DAGs in order
   dag_flavourflow_ingest → dag_flavourflow_stage →
   dag_flavourflow_transform → dag_flavourflow_dq
## Data Warehouse Location
SQL Server database: flavourflow_dw
Schemas: staging | dw
## Project Structure
See /sql/ddl for schema definitions
See /etl for standalone Python scripts
See /airflow/dags for orchestration