# Create a sample dashboard in ADX

1. Navigate to https://preview.dataexplorer.azure.com and login with your Microsoft account.

2. Click `Dashboards` in the left navigation menu.

![](..\images\LeftNav_Dashboards.png)

3. Click on `New dashboard` in the command bar.

![](..\images\CommandBar_NewDashboard.png)

4. Enter a name and click `Create`.

![](..\images\CreateNewDashboard.png)

5. Click `Add query`

![](..\images\AddQuery.png)

6. This should prompt you to add a data source. Enter the following details and click Connect:

- `Data source name`: `Github`
- `Cluster URI`: `https://demo11.westus.kusto.windows.net/`

7. Select `GitHub` from the database dropdown and click `Apply`.
   ![](..\images\DataSource.png)

8. Enter a query which you want to visualize and click `Run`.
   Example:

```
// WatchEvent is triggered when a repo is starred.
// Showing the top 5 popular repos by WatchEvent in the last week should give us a quick view into the hottest technologies
EventsAll
| where CreatedAt > ago(7d)
| where Type == "WatchEvent"
| summarize WatchEvents=count() by RepoName = tolower(tostring(Repo.name))
| top 5 by WatchEvents
```

9. Select `Pie Chart` as the `Visual type`.

![](..\images\PieChartVisualType.png)

10. Enter `Top 5 Repos` as the name for your tile and click `Done`.

![](..\images\TileTitleTop5Repos.png)

11. Click `Save`.

![](..\images\SampleDashboardWithFirstTile.png)

Congratulations! You have just created your first ADX dashboard with a single tile. You can find your dashboard later in the dashboard catalogue. Click `Dashboards` in the left navigation menu.

![](..\images\LeftNav_Dashboards.png)
