# SQL Filtering for Cybersecurity Analysis

## Project Description

As a cybersecurity analyst, I recently identified potential security issues related to after-hours login attempts. To investigate these incidents, I reviewed and queried the organization's login logs using SQL. Due to the high volume of data, I applied SQL filters to optimize the investigation process, ensuring a faster and more efficient retrieval of critical security information.

## Retrieve After-Hours Failed Login Attempts

To investigate failed login activity occurring after business hours (18:00), I queried the `log_in_attempts` table. I used SQL filters to isolate unsuccessful attempts:

```sql
SELECT * FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

This query utilizes the `AND` operator to satisfy two conditions: the login time must be after 18:00, and the `success` status must be 0 (indicating a failed attempt).

| event_id | username | login_date | login_time | country | ip_address     | success |
|----------|----------|------------|------------|---------|----------------|---------|
| 2        | apatel   | 2022-05-10 | 20:27:27   | CAN     | 192.168.205.12 | 0       |
| 18       | pwashing | 2022-05-11 | 19:28:50   | US      | 192.168.66.142 | 0       |
| 20       | tshah    | 2022-05-12 | 18:56:36   | MEXICO  | 192.168.109.50 | 0       |
| 28       | aestrada | 2022-05-09 | 19:28:12   | MEXICO  | 192.168.27.57  | 0       |
| 34       | drosas   | 2022-05-11 | 21:02:04   | US      | 192.168.45.93  | 0       |
| 42       | cgriffin | 2022-05-09 | 23:04:05   | US      | 192.168.4.157  | 0       |
| 52       | cjackson | 2022-05-10 | 22:07:07   | CAN     | 192.168.58.57  | 0       |
| 82       | abernard | 2022-05-12 | 23:38:46   | MEX     | 192.168.234.49 | 0       |
| 87       | apatel   | 2022-05-08 | 22:38:31   | CANADA  | 192.168.132.153| 0       |
| 96       | ivelasco | 2022-05-09 | 22:36:36   | CAN     | 192.168.84.194 | 0       |
| 104      | asundara | 2022-05-11 | 18:38:07   | US      | 192.168.96.200 | 0       |
| 107      | bisles   | 2022-05-12 | 20:25:57   | USA     | 192.168.116.187| 0       |
| 111      | aestrada | 2022-05-10 | 22:00:26   | MEXICO  | 192.168.76.27  | 0       |
| 127      | abellmas | 2022-05-09 | 21:20:51   | CANADA  | 192.168.70.122 | 0       |
| 131      | bisles   | 2022-05-09 | 20:03:55   | US      | 192.168.113.171| 0       |
| 155      | cgriffin | 2022-05-12 | 22:18:42   | USA     | 192.168.236.176| 0       |
| 160      | jclark   | 2022-05-10 | 20:49:00   | CANADA  | 192.168.214.49 | 0       |
| 199      | yappiah  | 2022-05-11 | 19:34:48   | MEXICO  | 192.168.44.232 | 0       |

## Retrieve Login Attempts on Specific Dates

To investigate a suspicious event, I filtered login records for May 9th, 2022, and the day prior. I utilized the `OR` operator to capture activity from both dates:

```sql
SELECT * FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

The query results display all login activity within the specified investigation window.

| event_id | username | login_date | login_time | country | ip_address     | success |
|----------|----------|------------|------------|---------|----------------|---------|
| 1        | jrafael  | 2022-05-09 | 04:56:27   | CAN     | 192.168.243.140| 1       |
| 3        | dkot     | 2022-05-09 | 06:47:41   | USA     | 192.168.151.162| 1       |
| 4        | dkot     | 2022-05-08 | 02:00:39   | USA     | 192.168.178.71 | 0       |
| 8        | bisles   | 2022-05-08 | 01:30:17   | US      | 192.168.119.173| 1       |
| 12       | dkot     | 2022-05-08 | 09:11:34   | US      | 192.168.100.158| 1       |
| 15       | lyamamot | 2022-05-09 | 17:17:26   | USA     | 192.168.183.51 | 0       |
| 24       | arusso   | 2022-05-09 | 06:49:39   | MEXICO  | 192.168.171.192| 1       |
| 25       | sbaelish | 2022-05-09 | 07:04:02   | US      | 192.168.33.137 | 1       |
| 26       | apatel   | 2022-05-08 | 17:27:00   | CANADA  | 192.168.123.105| 1       |
| 28       | aestrada | 2022-05-09 | 19:28:12   | MEXICO  | 192.168.27.57  | 0       |
| 30       | yappiah  | 2022-05-09 | 03:22:22   | MEX     | 192.168.124.48 | 1       |
| 32       | acook    | 2022-05-09 | 02:52:02   | CANADA  | 192.168.142.239| 1       |
| 36       | asundara | 2022-05-08 | 09:00:42   | US      | 192.168.78.151 | 1       |
| 38       | sbaelish | 2022-05-09 | 14:40:01   | US      | 192.168.60.42  | 1       |
| 39       | yappiah  | 2022-05-09 | 07:56:40   | MEXICO  | 192.168.57.115 | 1       |
| 42       | cgriffin | 2022-05-09 | 23:04:05   | US      | 192.168.4.157  | 0       |
| 43       | mcouluba | 2022-05-08 | 02:35:34   | CANADA  | 192.168.16.208 | 1       |
| 44       | daquino  | 2022-05-08 | 07:02:35   | CANADA  | 192.168.168.144| 0       |
| 47       | dkot     | 2022-05-08 | 05:06:45   | US      | 192.168.233.24 | 1       |
| 49       | asundara | 2022-05-08 | 14:00:01   | US      | 192.168.173.213| 0       |
| 53       | nmason   | 2022-05-08 | 11:51:38   | CAN     | 192.168.133.188| 1       |
| 56       | acook    | 2022-05-08 | 04:56:30   | CAN     | 192.168.209.130| 1       |
| 58       | ivelasco | 2022-05-09 | 17:20:54   | CAN     | 192.168.57.162 | 0       |
| 61       | dtanaka  | 2022-05-09 | 09:45:18   | USA     | 192.168.98.221 | 1       |
| 65       | aalonso  | 2022-05-09 | 23:42:12   | MEX     | 192.168.52.37  | 1       |
| 66       | aestrada | 2022-05-08 | 21:58:32   | MEX     | 192.168.67.223 | 1       |
| 67       | abernard | 2022-05-09 | 11:53:41   | MEX     | 192.168.118.29 | 1       |
| 68       | mrah     | 2022-05-08 | 17:16:13   | US      | 192.168.42.248 | 1       |
| 70       | tmitchel | 2022-05-09 | 10:55:17   | MEXICO  | 192.168.87.199 | 1       |
| 71       | mcouluba | 2022-05-08 | 06:57:42   | CAN     | 192.168.55.169 | 1       |
| 72       | alevitsk | 2022-05-08 | 12:09:10   | CANADA  | 192.168.139.176| 1       |
| 79       | abernard | 2022-05-09 | 11:41:15   | MEX     | 192.168.158.170| 1       |
| 80       | cjackson | 2022-05-08 | 02:18:10   | CANADA  | 192.168.33.140 | 1       |
| 83       | lrodriqu | 2022-05-08 | 08:10:23   | USA     | 192.168.67.69  | 1       |
| 87       | apatel   | 2022-05-08 | 22:38:31   | CANADA  | 192.168.132.153| 0       |
| 90       | gesparza | 2022-05-09 | 00:49:05   | CANADA  | 192.168.87.201 | 1       |
| 92       | pwashing | 2022-05-08 | 00:36:12   | US      | 192.168.247.219| 1       |
| 97       | jreckley | 2022-05-09 | 02:49:23   | MEXICO  | 192.168.32.231 | 1       |
| 101      | sbaelish | 2022-05-08 | 12:01:22   | US      | 192.168.145.158| 0       |
| 102      | jreckley | 2022-05-09 | 16:51:44   | MEX     | 192.168.108.13 | 1       |
| 108      | daquino  | 2022-05-08 | 21:30:48   | CANADA  | 192.168.15.110 | 1       |
| 110      | mabadi   | 2022-05-09 | 00:01:54   | USA     | 192.168.90.124 | 1       |
| 112      | rjensen  | 2022-05-09 | 09:22:05   | MEX     | 192.168.69.116 | 1       |
| 117      | bsand    | 2022-05-08 | 00:19:11   | USA     | 192.168.197.187| 1       |
| 120      | tmitchel | 2022-05-09 | 02:58:17   | MEXICO  | 192.168.134.62 | 0       |
| 127      | abellmas | 2022-05-09 | 21:20:51   | CANADA  | 192.168.70.122 | 0       |
| 128      | jclark   | 2022-05-09 | 10:45:59   | CANADA  | 192.168.122.169| 0       |
| 131      | bisles   | 2022-05-09 | 20:03:55   | US      | 192.168.113.171| 0       |
| 134      | iuduike  | 2022-05-09 | 06:46:40   | USA     | 192.168.22.115 | 1       |
| 135      | bsand    | 2022-05-09 | 14:06:33   | US      | 192.168.91.238 | 0       |
| 144      | daquino  | 2022-05-09 | 11:09:32   | CANADA  | 192.168.139.9  | 1       |
| 145      | ivelasco | 2022-05-08 | 09:06:02   | CANADA  | 192.168.39.196 | 1       |
| 147      | yappiah  | 2022-05-08 | 06:04:34   | MEX     | 192.168.65.245 | 1       |
| 148      | daquino  | 2022-05-08 | 06:15:55   | CAN     | 192.168.135.6  | 1       |
| 150      | nmason   | 2022-05-08 | 14:40:02   | CAN     | 192.168.204.124| 1       |
| 151      | mabadi   | 2022-05-09 | 16:29:46   | USA     | 192.168.30.225 | 1       |
| 158      | sglimore | 2022-05-08 | 12:27:22   | CAN     | 192.168.52.216 | 0       |
| 184      | alevitsk | 2022-05-08 | 03:09:48   | CAN     | 192.168.33.70  | 0       |
| 186      | bisles   | 2022-05-09 | 04:29:17   | USA     | 192.168.40.72  | 0       |
| 187      | arusso   | 2022-05-09 | 00:36:26   | MEX     | 192.168.77.137 | 0       |
| 189      | nmason   | 2022-05-08 | 05:37:24   | CANADA  | 192.168.168.117| 1       |
| 190      | jsoto    | 2022-05-09 | 05:09:21   | USA     | 192.168.25.60  | 0       |
| 191      | cjackson | 2022-05-08 | 06:46:07   | CANADA  | 192.168.7.187  | 0       |
| 193      | lrodriqu | 2022-05-08 | 07:11:29   | US      | 192.168.125.240| 0       |
| 197      | jsoto    | 2022-05-08 | 09:05:09   | US      | 192.168.36.21  | 0       |

## Retrieve Login Attempts Outside of Mexico

My investigation revealed suspicious activity originating from outside of Mexico. To isolate these records, I used the `NOT` operator combined with `LIKE` and the `%` wildcard. This ensured the exclusion of all login attempts from Mexico, regardless of the naming convention used in the logs (e.g., 'MEX' or 'MEXICO').

```sql
SELECT * FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

The query output displays all login attempts originating from any country recorded in the logs, excluding Mexico.

| event_id | username | login_date | login_time | country | ip_address     | success |
|----------|----------|------------|------------|---------|----------------|---------|
| 2        | apatel   | 2022-05-10 | 20:27:27   | CAN     | 192.168.205.12 | 0       |
| 18       | pwashing | 2022-05-11 | 19:28:50   | US      | 192.168.66.142 | 0       |
| 34       | drosas   | 2022-05-11 | 21:02:04   | US      | 192.168.45.93  | 0       |
| 42       | cgriffin | 2022-05-09 | 23:04:05   | US      | 192.168.4.157  | 0       |
| 52       | cjackson | 2022-05-10 | 22:07:07   | CAN     | 192.168.58.57  | 0       |
| 69       | wjaffrey | 2022-05-11 | 19:55:15   | USA     | 192.168.100.17 | 1       |
| 87       | apatel   | 2022-05-08 | 22:38:31   | CANADA  | 192.168.132.153| 0       |
| 96       | ivelasco | 2022-05-09 | 22:36:36   | CAN     | 192.168.84.194 | 0       |
| 104      | asundara | 2022-05-11 | 18:38:07   | US      | 192.168.96.200 | 0       |
| 107      | bisles   | 2022-05-12 | 20:25:57   | USA     | 192.168.116.187| 0       |
| 131      | bisles   | 2022-05-09 | 20:03:55   | US      | 192.168.113.171| 0       |
| 155      | cgriffin | 2022-05-12 | 22:18:42   | USA     | 192.168.236.176| 0       |
| 160      | jclark   | 2022-05-10 | 20:49:00   | CANADA  | 192.168.214.49 | 0       |
| 156      | btang    | 2022-05-11 | 17:08:51   | USA     | 192.168.243.95 | 0       |
| 159      | iuduike  | 2022-05-12 | 16:59:50   | USA     | 192.168.220.115| 1       |
| 161      | abellmas | 2022-05-09 | 13:25:50   | CAN     | 192.168.180.205| 0       |
| 164      | jclark   | 2022-05-12 | 21:15:52   | CAN     | 192.168.18.34  | 1       |
| 167      | jclark   | 2022-05-12 | 15:47:45   | CAN     | 192.168.146.51 | 1       |
| 168      | jlansky  | 2022-05-08 | 13:25:42   | USA     | 192.168.210.94 | 1       |
| 169      | alevitsk | 2022-05-08 | 08:10:43   | CANADA  | 192.168.210.228| 0       |
| 170      | sbaelish | 2022-05-09 | 16:43:18   | US      | 192.168.65.113 | 1       |
| 171      | drosas   | 2022-05-10 | 16:32:55   | US      | 192.168.92.218 | 1       |
| 172      | mabadi   | 2022-05-08 | 08:06:50   | US      | 192.168.180.41 | 1       |
| 173      | asundara | 2022-05-12 | 23:17:52   | US      | 192.168.58.217 | 1       |
| 174      | lyamamot | 2022-05-10 | 12:26:27   | US      | 192.168.228.122| 1       |
| 175      | jhill    | 2022-05-10 | 00:17:09   | USA     | 192.168.130.218| 0       |
| 177      | wjaffrey | 2022-05-11 | 00:15:55   | USA     | 192.168.144.165| 0       |
| 178      | sglimore | 2022-05-08 | 12:27:22   | CAN     | 192.168.52.216 | 0       |
| 179      | jclark   | 2022-05-12 | 04:08:17   | CAN     | 192.168.232.93 | 0       |
| 181      | abellmas | 2022-05-10 | 13:37:05   | CAN     | 192.168.60.111 | 0       |
| 182      | lyamamot | 2022-05-10 | 06:01:31   | USA     | 192.168.106.52 | 0       |
| 183      | nmason   | 2022-05-11 | 05:29:36   | CANADA  | 192.168.137.147| 1       |
| 184      | alevitsk | 2022-05-08 | 03:09:48   | CAN     | 192.168.33.70  | 0       |
| 185      | jsoto    | 2022-05-10 | 13:34:58   | USA     | 192.168.151.91 | 0       |
| 186      | bisles   | 2022-05-09 | 04:29:17   | USA     | 192.168.40.72  | 0       |
| 188      | jsoto    | 2022-05-11 | 00:39:09   | USA     | 192.168.21.88  | 0       |
| 189      | nmason   | 2022-05-08 | 05:37:24   | CANADA  | 192.168.168.117| 1       |
| 190      | jsoto    | 2022-05-09 | 05:09:21   | USA     | 192.168.25.60  | 0       |
| 191      | cjackson | 2022-05-08 | 06:46:07   | CANADA  | 192.168.7.187  | 0       |
| 192      | bisles   | 2022-05-10 | 08:32:03   | US      | 192.168.201.40 | 1       |
| 193      | lrodriqu | 2022-05-08 | 07:11:29   | US      | 192.168.125.240| 0       |
| 194      | jclark   | 2022-05-12 | 14:11:04   | CAN     | 192.168.197.247| 0       |
| 195      | alevitsk | 2022-05-11 | 06:59:13   | CAN     | 192.168.236.78 | 1       |
| 196      | acook    | 2022-05-10 | 09:56:48   | CAN     | 192.168.52.90  | 0       |
| 197      | jsoto    | 2022-05-08 | 09:05:09   | US      | 192.168.36.21  | 0       |
| 200      | jclark   | 2022-05-12 | 01:11:45   | CANADA  | 192.168.91.103 | 1       |

## Retrieve Employees in Marketing (East Building)

The organization is implementing security updates for employee devices within the Marketing department, specifically those located in the East building. I performed a query to retrieve information on these specific machines, using the `AND` operator and the `LIKE` filter with a wildcard to capture all variations of East building office numbers (e.g., East-170, East-320).

```sql
SELECT * FROM employees
WHERE department = 'Marketing' AND office LIKE 'East-%';
```

The results provide comprehensive data for all employee devices in the Marketing department situated in the East building.

| employee_id | device_id   | username | department | office    |
|-------------|-------------|----------|------------|-----------|
| 1000        | a320b137c219| elarson  | Marketing  | East-170  |
| 1052        | a192b174c940| jdarosa  | Marketing  | East-195  |
| 1075        | x573y883z772| fbautist | Marketing  | East-267  |
| 1088        | k8651965m233| rgosh    | Marketing  | East-157  |
| 1103        | NULL        | randerss | Marketing  | East-460  |
| 1156        | a184b775c707| dellery  | Marketing  | East-417  |
| 1163        | h679i515j339| cwilliam | Marketing  | East-216  |

## Retrieve Employees in Finance or Sales

A different security update is required for devices in either the Finance or Sales departments. I executed an SQL query using the `OR` operator to identify all employees belonging to these two specific departments.

```sql
SELECT * FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

| employee_id | device_id   | username  | department | office      |
|-------------|-------------|-----------|------------|-------------|
| 1089        | l358m929n154| jpark2    | Sales      | West-251    |
| 1091        | n378o313p469| rtran     | Sales      | Central-230 |
| 1092        | o391p779q935| lpark     | Sales      | West-227    |
| 1098        | u671v14w618 | tcharamb  | Finance    | North-423   |
| 1099        | v283w690x104| anaser    | Finance    | West-357    |
| 1105        | b551c837d758| kmei      | Finance    | Central-232 |
| 1107        | d168e758f876| akajwara  | Finance    | North-471   |
| 1109        | f229g533h679| nlocklea  | Sales      | East-196    |
| 1110        | g567h376i314| pchaudh   | Sales      | Central-428 |
| 1111        | h8351179j862| jlee      | Sales      | West-309    |
| 1116        | m272n572o874| nzhao     | Sales      | South-100   |
| 1117        | n683o758p820| dahmad    | Sales      | North-405   |
| 1118        | o305p208q337| jpark3    | Sales      | South-329   |
| 1119        | p164q780r999| omubarak  | Sales      | North-409   |
| 1121        | r628s557t397| mrojas    | Sales      | East-288    |
| 1122        | s103t952u851| btorres   | Finance    | West-319    |
| 1130        | a317b635c465| tsnow     | Sales      | Central-451 |
| 1136        | g299h520i457| jhawes    | Finance    | West-416    |
| 1138        | i671j355k725| sromero   | Finance    | South-329   |
| 1142        | m674n127o823| lsilva    | Finance    | East-440    |
| 1144        | NULL        | erobinso  | Finance    | Central-266 |
| 1147        | r454s225t299| tvega     | Finance    | West-177    |
| 1148        | s328t505u907| dharvey   | Finance    | South-181   |
| 1149        | d881e710f732| jshen     | Finance    | East-193    |
| 1164        | i682j513k442| fsmeltz   | Finance    | North-163   |
| 1169        | NULL        | mmitchel  | Sales      | Central-250 |
| 1174        | s371t911u987| eortiz    | Finance    | North-428   |
| 1175        | t959u687v394| jclark2   | Finance    | North-194   |
| 1176        | u849v56w521 | nliu      | Sales      | West-220    |
| 1181        | z803a233b718| sessa     | Sales      | South-207   |
| 1185        | d790e839f461| revens    | Sales      | North-330   |
| 1186        | e281f433g404| sacosta   | Sales      | North-460   |
| 1187        | f963g637h851| bbode     | Finance    | East-351    |
| 1188        | g164h566i795| noshiro   | Finance    | West-252    |
| 1195        | n516o853p957| orainier  | Finance    | East-346    |

## Retrieve All Employees Not in IT

The organization requires a comprehensive security update for all departments except Information Technology, as their systems are already up to date. I used the `NOT` operator to retrieve information for all employees across all departments, specifically excluding the IT department.

```sql
SELECT * FROM employees
WHERE NOT department = 'Information Technology';
```

This successfully filters the employee list to exclude the Information Technology department, ensuring the update is targeted correctly.

| employee_id | device_id   | username  | department       | office      |
|-------------|-------------|-----------|------------------|-------------|
| 1157        | b264c773d977| lstein    | Human Resources  | Central-343 |
| 1158        | c406d877e950| bnaser    | Human Resources  | Central-243 |
| 1159        | d881e710f732| jshen     | Finance          | East-193    |
| 1160        | e127f591g924| spham     | Marketing        | West-353    |
| 1163        | h679i515j339| cwilliam  | Marketing        | East-216    |
| 1164        | i682j513k442| fsmeltz   | Finance          | North-163   |
| 1165        | j713k893i832| nwords    | Marketing        | South-128   |
| 1166        | k4951234m708| nyoung    | Marketing        | Central-397 |
| 1167        | t738m922n515| tblackwe  | Marketing        | North-443   |
| 1169        | NULL        | mmitchel  | Sales            | Central-250 |
| 1170        | o156p302q359| lalvarez  | Human Resources  | North-278   |
| 1172        | q372r826s628| akhan     | Marketing        | Central-360 |
| 1173        | r537s849t690| ialcazar  | Finance          | South-429   |
| 1174        | s371t911u987| eortiz    | Finance          | North-428   |
| 1175        | t959u687v394| jclark2   | Finance          | North-194   |
| 1176        | u849v56w521 | nliu      | Sales            | West-220    |
| 1177        | v691w183x928| aezra     | Human Resources  | East-190    |
| 1178        | w986x187y885| nlannist  | Marketing        | North-196   |
| 1179        | x174y934z376| asalas    | Human Resources  | North-445   |
| 1180        | y131z2211a578| medwards  | Human Resources  | Central-340 |
| 1181        | z803a233b718| sessa     | Finance          | South-207   |
| 1183        | b566c710d544| lquraish  | Human Resources  | East-400    |
| 1184        | c986d200e170| ptsosie   | Human Resources  | Central-247 |
| 1185        | d790e839f461| revens    | Sales            | North-330   |
| 1186        | e281f433g404| sacosta   | Sales            | North-460   |
| 1187        | f963g637h851| bbode     | Finance          | East-351    |
| 1188        | g164h566i795| noshiro   | Finance          | West-252    |
| 1190        | NULL        | kcarter   | Marketing        | Central-270 |
| 1191        | NULL        | shakimi   | Marketing        | Central-366 |
| 1194        | m340n287o441| zwarren   | Human Resources  | West-212    |
| 1195        | n516o853p957| orainier  | Finance          | East-346    |
| 1198        | q308r573s459| jmartine  | Marketing        | South-117   |
| 1199        | r520s571t459| areyes    | Human Resources  | East-100    |

## Summary

This project demonstrates the effectiveness of using advanced SQL filters (`AND`, `OR`, `NOT`, `LIKE`) in the context of cybersecurity analysis. By applying these techniques, analysts can narrow down large datasets to identify suspicious patterns, track security incidents, and efficiently gather critical security intelligence. This capability is essential for maintaining a strong security posture and responding quickly to potential threats in complex data environments.
