# 3 - Add a tile to the dashboard by pinning a query

1. Navigate to the `Query` experience and add the same cluster used earlier

- `Cluster URI`: `https://demo11.westus.kusto.windows.net/`
- `Database`: `GitHub`

![](../images/LeftNav_Query_AddCluster.png)

2. Write a query to visualize the popularity trend of vscode and typescript over last three years

```
   EventsAll
   | where Repo.name =~ "Microsoft/vscode" or Repo.name =~ "Microsoft/TypeScript"
   | make-series count() default=0 on CreatedAt in range(datetime(2016-01-01), datetime(2019-06-11), 30d) by RepoName = tolower(tostring(Repo.name))
   | project CreatedAt, RepoName, count_
```

3. To add the query to our existing dashboard, click the `Pin to dashboard` option in the `Share` menu.

![](../images/Share_PinToDashboard.png)

4. Enter the details, as shown below and click `Pin`.

![](../images/PinToDashboard.png)

5. The newly added visual now appears on your dashboard. By default, the tile shows a table visual. Edit it to make it an Area chart and save your dashboard. It should look as shown below.

![](../images/SampleDashboardWithPinnedTile.png)

# Go back to [2 - Add additional tiles by cloning existing tiles](2-CloneTile.md) or proceed to [4 - Explore data on existing tiles in a dashboard](4-Explore.md)
