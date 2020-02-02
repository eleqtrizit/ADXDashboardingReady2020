# Create and use a parameter in query and dashboard

1. Click the browser `Back` button to navigate back to your dashboard. Alternatively, you can click `Dashboards` in the left navigation menu and then click on your dashboard.

2. Click `Edit` to enter edit mode.

3. Click `Add Parameter` in the dashboard command bar.

4. Select the `Query Values` pivot.

5. Enter `MSRepo` as the `Variable name` and `Microsoft Repo` as the `Display name`.

6. Select `Github` as the `Data source`.

7. Enter the following query:

```
EventsAll
| where Repo.name has 'Microsoft'
| summarize TotalEvents = count() by RepoName=tostring(Repo.name)
| top 5 by TotalEvents
| project RepoName
```

![](../images/Parameter_Query.png)

8. Click `Run query` and select `Microsoft/vscode` as the `Default value`.

9. Click `Done`. You should now see this parameter next to the Time range picker.

10. Clone the `Popularity of vscode and TypeScript` tile and edit it's query to use the newly created parameter and save it as a `Time Chart`.

```
EventsAll
| where Repo.name == MSRepo
| make-series count() default=0 on CreatedAt in range(datetime(2016-01-01), datetime(2019-06-11), 30d) by RepoName = tolower(tostring(Repo.name))
| project CreatedAt, RepoName, count_
```

11. Change the value of the parameter in the dashboard to see the chart update.

![](../images/ParameterInDashboard.png)
