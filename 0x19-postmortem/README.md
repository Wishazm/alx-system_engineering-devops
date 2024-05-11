# PostMortem

## Issue Summary:
- **Duration:** May 10, 2024, 08:00 UTC to May 10, 2024, 12:00 UTC
- **Impact:** Service downtime; all users experienced inability to access the platform; 100% of users affected.
- **Root Cause:** Database connection pool exhaustion due to unoptimized query execution.

## Timeline:
- **08:00 UTC:** Issue detected through a spike in error rates on monitoring dashboard.
- **08:05 UTC:** Engineers noticed degraded system performance.
- **08:10 UTC:** Investigation began on the database layer assuming database overload.
- **09:00 UTC:** Misleadingly focused on scaling database servers.
- **10:00 UTC:** Incident escalated to senior engineers and database administrators.
- **11:00 UTC:** Root cause identified as inefficient database queries.
- **12:00 UTC:** Issue resolved by optimizing database queries and increasing connection pool size.

## Root Cause and Resolution:
The root cause of the outage was identified as unoptimized database queries leading to connection pool exhaustion. This occurred due to a recent update in the application code which inadvertently introduced inefficient query patterns. As a result, the database server was overwhelmed with concurrent connections, causing the system to become unresponsive.

To resolve the issue, engineers optimized the problematic queries by adding appropriate indexes and rewriting SQL statements for better efficiency. Additionally, the connection pool size was increased to handle the sudden surge in connections during peak usage hours. These measures alleviated the strain on the database server and restored normal system functionality.

## Corrective and Preventative Measures:
To prevent similar incidents in the future, the following measures will be implemented:
1. **Code Review Process Enhancement:** Strengthen the code review process to detect and address inefficient query patterns before deployment.
2. **Automated Testing:** Implement automated performance testing to identify potential bottlenecks in database queries during the CI/CD pipeline.
3. **Monitoring and Alerting:** Enhance monitoring and alerting systems to provide early detection of database performance issues, enabling proactive intervention.
4. **Documentation Update:** Update documentation to educate developers on best practices for writing efficient database queries.
5. **Regular Performance Reviews:** Conduct regular performance reviews of database queries to identify optimization opportunities and ensure efficient resource utilization.

## Tasks:
1. Update code review checklist to include database query optimization.
2. Implement automated performance testing using tools like JMeter or Gatling.
3. Configure additional monitoring checks for database connection pool utilization.
4. Schedule training sessions for developers on writing efficient SQL queries.
5. Conduct quarterly performance reviews of critical database queries and optimize as needed.

**By implementing these corrective and preventative measures, we aim to fortify our system against similar incidents in the future, ensuring uninterrupted service for our users.**
