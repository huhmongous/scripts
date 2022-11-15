import boto3

rds = boto3.client('rds')

db = rds.describe_db_instances()

rds_dbinstances = db['DBInstances']


for dba in rds_dbinstances:
    if dba['PerformanceInsightsEnabled']  == False:
        try:
            response = rds.modify_db_instance(
                DBInstanceIdentifier=dba['DBInstanceIdentifier'],
                EnablePerformanceInsights=True,
            )
        except Exception as e:
            print(dba['DBInstanceIdentifier'], "error enabling Performance Insights")
