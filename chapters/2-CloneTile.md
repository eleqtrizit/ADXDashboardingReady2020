# 2 - Add additional tiles by cloning existing tiles

1. Switch to Edit mode on your dashboard by clicking `Edit` on the top right of the command bar.

![](../images/CommandBar_Edit.png)

2. Click `Clone tile` on the `Top 5 Repos` tile to duplicate it.

![](../images/TileActions_Clone.png)

3. Click `Edit tile` to update the query.

```
// Lets' see what Microsoft technologies have the most traction in GitHub
EventsAll
| where Repo.name has 'Microsoft'
| summarize TotalEvents = count() by RepoName=tolower(tostring(Repo.name))
| top 5 by TotalEvents
```

4. Update the query to work with the `Time range` picker by using the keywords `startTime` and `endTime` in your query.

![](../images/TimeRangePicker.png)

```
// Lets' see what other Microsoft technologies have the most traction in GitHub
EventsAll
| where Repo.name has 'Microsoft'
| where CreatedAt between (startTime..endTime)
| summarize TotalEvents = count() by RepoName=tostring(Repo.name)
| top 5 by TotalEvents
```

5. Save as a `Column` chart and name it `Top Microsoft Technologies`.

6. Resize and place this tile next to your previous tile and save your dashboard.

![](../images/SampleDashboardWithSecondTile.png)

7. Play with the time range picker and notice how the bar chart reflects the selected time range.

# Go back to [1 - Create a sample dashboard](1-CreateSampleDashboard.md) or proceed to [3 - Add tiles by pinning a query to a dashboard](3-PinQuery.md)
