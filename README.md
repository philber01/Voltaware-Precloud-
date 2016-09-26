# Voltaware-Precloud-
Includes signature cluster and voltaware.py
The installation procedure consists in the following steps:

1.	Preparation of a new sensor with no pre-existing pre-cloud or cloud data, ideally starting in pre-live mode with the ML progress bar.
2.	Creation of a tar file of the folders ~/list_mqtt_sensors, ~/svmV3 with all the subfolders Clustering, SVM, logs, csv/barycenters, csv/clusters, csv/ref_vectors, csv/samples, csv/taus , ~/signature and ~/signature/disaggregation.
3.	Copying the tar file in the /home/Ubuntu folder of a Ubuntu server running the required libraries as detailed in the section 3.
4.	Extraction of the tar file at the root level /home/Ubuntu
5.	Compilation of signature and cluster: cd signature ; make
6.	In the event that the new server is running all the sensors of the dev environment for instance, there is an addition of the following entries in the crontab:
0   *  *  *  *   /bin/bash -x /home/ubuntu/list_mqtt_sensors/sign.sh >> /var/log/pcloud/sign.log 2>> /var/log/pcloud/sign.log
15  *  *  *  *   /bin/bash -x /home/ubuntu/list_mqtt_sensors/sign.sh >> /var/log/pcloud/sign.log 2>> /var/log/pcloud/sign.log
30  *  *  *  *   /bin/bash -x /home/ubuntu/list_mqtt_sensors/sign.sh >> /var/log/pcloud/sign.log 2>> /var/log/pcloud/sign.log
45  *  *  *  *   /bin/bash -x /home/ubuntu/list_mqtt_sensors/sign.sh >> /var/log/pcloud/sign.log 2>> /var/log/pcloud/sign.log
If it is running only one sensor the script sign.sh would have to be adapted to run only one instance of the signature program.
7.	In the case of a new sensor the sensor file sensor00.csv will be copied as sensorXYZT.csv with default values.
8.	After the cron starts the script sign.sh checking of the process running with at least disaggregation.sh, sign.sh and one instance of signature. If it does not start automatically it is recommended to start the command manually.
9.	The mobile application should immediately (in less than 3 minutes) show the latest reading.
10.	Machine learning for around 10 days, if the problem detailed as “Sample Holes” below does not slow the acquisition process. Monitoring the progress by checking the 4th field of the sensorXYZT.csv file.
11.	After the ML completion, tagging of the appliances found by the system and showing up in the app.
12.	After an additional 10 days, promotion and demotion of the appliances of the 2nd generation. 
