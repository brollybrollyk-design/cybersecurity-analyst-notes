# SQL for Security Investigations

## Purpose
SQL is commonly used to analyze authentication logs and user activity stored in databases in order to detect potential security incidents.

## Example Queries

### Failed Login Attempts
SELECT user, COUNT(*) AS failed_attempts
FROM authentication_logs
WHERE status = 'FAILED'
GROUP BY user
HAVING COUNT(*) > 5;

### Logins Outside Normal Hours
SELECT user, login_time
FROM authentication_logs
WHERE login_time NOT BETWEEN '08:00' AND '18:00';

### Suspicious IP Activity
SELECT source_ip, COUNT(*) AS attempts
FROM authentication_logs
GROUP BY source_ip
ORDER BY attempts DESC;

## Security Value
These queries help identify abnormal authentication behavior such as brute-force attempts, compromised credentials, and suspicious access patterns.
