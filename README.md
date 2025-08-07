🧪 DQC Automation Testing
A Python-based Data Quality Check (DQC) automation tool that connects to a PostgreSQL database, inspects a target table (employees), and generates column-wise quality metrics such as null counts, distinct counts, uniqueness ratios, and example values. Built with pandas, SQLAlchemy, and DuckDB.

📌 Features
✅ Connects to PostgreSQL using SQLAlchemy

📋 Extracts schema metadata from the employees table

🧠 Dynamically generates SQL for:

Null values

Empty strings (for text columns)

Distinct counts

Example values

Min/Max for numeric and date fields

⚙️ Robust error handling for each column query

📊 Generates a final summary DataFrame

🔍 Identifies columns with high null rates and low uniqueness

🔧 Requirements
Install dependencies using pip:

bash
Copy
Edit
pip install pandas sqlalchemy duckdb psycopg2-binary
🛠️ Configuration
Set your PostgreSQL credentials by editing or importing from the postgresql1 module:

python
Copy
Edit
from postgresql1 import host, database, port, username, password
🚀 How It Works
Connect to PostgreSQL and DuckDB.

Query schema info for the employees table from PostgreSQL.

Generate dynamic SQL to check data quality metrics for each column.

Execute each query safely, catching errors per column.

Combine and display results, including:

Total rows

Null/Empty counts

Uniqueness ratio

Min/Max values (for numeric/date columns)

Show additional insights, such as:

Columns with the most nulls

Columns with lowest uniqueness

📊 Example Output
plaintext
Copy
Edit
📋 Found 8 columns in the employees table

🚀 Running DQC on 8 columns...

📊 === Data Quality Summary ===
  column_name | column_type | null_count | distinct_count | ...

📈 === Additional Insights ===
Total rows in table: 10,000

Columns with highest null percentages:
 • address: 24.6%
 • phone: 17.2%

Columns with low uniqueness (potential duplicates):
 • department_id: 0.06 ratio
 • job_title: 0.21 ratio
🧹 Cleanup
At the end of execution, all connections to databases are properly closed:

python
Copy
Edit
engine1.dispose()
con.close()
📁 File Structure
bash
Copy
Edit
📦 dqc_automation_testing
┣ 📜 main.py              # Core DQC script
┣ 📜 postgresql1.py       # PostgreSQL credentials
┣ 📜 README.md            # Project documentation
