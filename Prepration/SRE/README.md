1) What is the role of an SRE in a product engineering company?

```
An SRE ensures that the product is reliable, scalable, and always available for users.
They automate operations, monitor systems, handle production issues, and work closely with developers
so new features can be released safely without impacting reliability
```
2) How is SRE different from DevOps in real projects?
```
DevOps is about culture and automation, while SRE is about applying engineering to keep systems reliable and scalable.
```
3) How do you implement SLOs for customer-facing applications?
```
First, I identify what users care about, like availability and latency.
Second, I set clear SLO targets, for example 99.9% responses under 300ms.
Third, I monitor and alert on SLOs using tools like Prometheus or Grafana.
Fourth, I use error budgets to control risk and slow releases if needed.
Finally, I review incidents and improve based on user impact.
```
4) What is an error budget and how do you use it practically?
```
An error budget is the amount of acceptable failure a system can have while still meeting its SLO.
It is calculated from the SLO and is used to balance reliability and speed of change
```
5) How do you measure reliability in production?
```
I measure reliability using user-focused metrics called SLIs like availability, latency, and error rate.
Then I set SLO targets, monitor them with tools like Prometheus or Grafana,
use error budgets to control risk, and continuously improve based on incidents.
```
6) How do you reduce operational toil?
```
I reduce operational toil by automating repetitive tasks.
For example, I’ve written small scripts to help with deployments and set up alerts so
I don’t have to manually check systems all the time. This way,
I can focus more on solving real problems instead of doing the same manual work over and over.
```
7) When do you say NO to a release?
```
I would say no to a release if the system is unstable or key SLOs are not being met. For example,
if the error budget is exhausted, critical alerts are failing, or production incidents are happening,
I would pause the release until the issues are resolved to avoid impacting users.
```
8) How do you bring reliability culture to dev teams?
```
I bring a reliability culture to dev teams by sharing metrics and making reliability visible. For example,
I track SLOs and error budgets and discuss them in team meetings so everyone knows how their code affects users.
I also suggest small improvements, like adding monitoring, alerts, or automated tests,
and encourage teams to fix issues proactively before they become outages.
```
