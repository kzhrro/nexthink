<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <h1>Memory and CPU usage - Nexthink Infinity (classic)</h1>
</head>
  <body>
<p>Efficiently managing hardware resources is essential for assessing device performance and its impact on the overall employee experience. This article provides insights into memory and Central Processing Unit (CPU) usage within the Nexthink Infinity platform, offering detailed metrics and explanations for effective resource allocation.
</p>
<h2>Memory usage</h2>
<h3>Sampling approach</h3>
<p>Nexthink utilizes a sampling approach to measure memory usage. The device's CPU usage level is reported every 1 minute, providing 2 samples within each 30-second interval. Subsequently, this data is aggregated into 5-minute intervals using the aggregation service and further condensed into 15-minute time buckets.
For Execution Events, CPU time is reported every 5 minutes after the creation of a process, consisting of 10 samples at 30-second intervals. It is essential to note that this data may overlap with the CPU blocks related to device performance. Additionally, this information is also provided upon process termination. However, it is crucial to be aware that the last set of data may only represent the initial 0-5 minutes of the execution.
</p>
<h3>Memory metrics details</h3>
<table>
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Applies to</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>Average memory usage per execution</td>
        <td>Aggregate</td>
        <td>User, device, application, executable, binary</td>
        <td>The average memory usage of all underlying executions divided by their cardinality.</td>
    </tr>
    <tr>
        <td>Average memory usage (deprecated)</td>
        <td>Field</td>
        <td>Binary</td>
        <td>The average memory usage of the underlying execution with a sampling rate of 5 minutes.</td>
    </tr>
    <tr>
        <td>Average memory usage</td>
        <td>Field</td>
        <td>Execution</td>
        <td>The average memory usage of the execution before aggregation.</td>
    </tr>
</table>
<p><i>Note: Nexthink calculates memory usage per process before potential aggregation, considering scenarios where a single binary may spawn multiple identical processes, resulting in higher total memory consumption.
</i></p>

<h2>CPU usage</h2>
<h3>CPU load samples</h3>
<p>For CPU usage, the Collector captures CPU load samples of all running processes every 30 seconds. Unlike memory usage, these samples are not averaged before transmission to Engine, allowing Engine to recognize peaks in CPU utilization.
</p>
<h3>CPU metrics details</h3>
<table>
  <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Applies to</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>Total CPU time</td>
        <td>Field</td>
        <td>Execution</td>
        <td>The effective utilization time of the CPU during the aggregated execution. Note: It can exceed the total duration of the execution if the average CPU load was over 100%.</td>
    </tr>
    <tr>
        <td>Total CPU time (aggregate)</td>
        <td>Aggregate</td>
        <td>User, device, application, executable, binary</td>
        <td>The sum of the total CPU time of all executions within the scope of the selected object.</td>
    </tr>
    <tr>
        <td>CPU usage ratio</td>
        <td>Aggregate</td>
        <td>User, device, application, executable, binary</td>
        <td>The sum of the total CPU time of all executions divided by their duration within the scope of the selected object.</td>
    </tr>
    <tr>
        <td>Average CPU usage (deprecated)</td>
        <td>Field</td>
        <td>Binary</td>
        <td>Average CPU load of a binary over all logical processors, taking into account all its executions since the binary was first seen. Note that this value does not depend on the selected time frame.</td>
    </tr>
</table>
<p><i>Note: The CPU usage values are directly derived from running processes. Additionally, the Collector captures samples of the total CPU load reported by a device, not broken down by processes, to indicate high CPU conditions.
</i></p>
</body>
</html>
