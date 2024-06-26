# Fabric WhoIsActive
Fabric sp_WhoIsActive for real time SQL Monitoring
Monitoring TSQL Script for Fabric DW with similar output to https://whoisactive.com/ which is created and maintained by fellow MCM 
<a href="https://github.com/amachanic">Adam Machanic</a>, - probably the most widely used and known 3rd Party scripot for SqlDbEngine

If you haven't installed sp_WhoIsActive on all your SqlDbEngine, then its a must install. Adam's code is a master class in 
design, TSQL coding and extensibility. A lesson in how to go from a basic script to a swiss army knife for instant performance and monitoring ;-)

This Fabric DW script just shows exec requests, sessions and SQL Statements. When coming from SqlDbEngine this adds some familiarity to monitoring.

Maybe in the future we will use KQL and Log Analytics, but hopefully we get more DMVs to expand this type of solution.

Features:
- long runing queries
- view query text
- reads and writes
- blocking chains
- some wait stat info
- *new* shows percent complete and eta for queries based on last run in QueryInsights history

Limitations:
- We dont yet have query plans in Fabric DW
- Wait stats are pretty generic
- We dont get CPU in DMVs
- No XML or ring buffer support in Fabric
- QueryInsights data is only from current DB, not system wide.
- The following DMVS we use on SqlDBEngine are not supported on Fabric
  - sys.dm_os_sys_info
  - sys.dm_os_workers
  - sys.dm_os_threads
  - sys.dm_os_waiting_tasks
  - sys.dm_db_task_space_usage
  - sys.dm_tran_active_transactions
  - sys.dm_tran_database_transactions
  - sys.dm_tran_session_transactions
  - sys.dm_exec_query_statistics_xml
  - sys.dm_exec_text_query_plan
  - sys.dm_broker_activated_tasks
  - sys.dm_os_tasks
  - sys.dm_os_waiting_tasks
  - sys.dm_db_session_space_usage



Sample call below showing a long running query causing blocking
![image](https://github.com/ProdataSQL/FabricWhoIsActive/assets/19823837/9aaed6f8-8940-41be-995e-371bf3ab8d7b)


