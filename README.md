# About mysql-log-maintenance
Linux has a utility called “logrotate” , using logrotate we can implement log rotation for any log file.
We can schedule mysql log rotation on the basis of size,time or both using mysql-logrotate script on linux platform.

#################
# Prerequisites #
#################

MYSQL USER and Privileges:
Example:

CREATE USER  'logadmin'@'localhost' IDENTIFIED BY 'xyzpwd';

GRANT RELOAD ON *.* TO 'logadmin'@'localhost';

######################################################
# Secure user credentials using mysql_config_editor: # 
######################################################
mysql_config_editor set --login-path=logadmin_client --host=localhost --user=monitor --password shekl

Enter password: enter_mysql_logadmin_user_password

####################
# Crontab          #
####################
Example:

00 03 * * * /usr/sbin/logrotate -s /PATH>/log/logrotate.status /PATH/mysql-log-rotate.sh > /PATH/log/logrotate_cron.log 2>&1
