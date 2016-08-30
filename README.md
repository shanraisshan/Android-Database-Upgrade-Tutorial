# Android-Database-Upgrade-Tutorial
This guide explains that how you can alter your database and add new column on each of your application release, without losing data.

Defination
----
**1. Fresh Install:**
in this scenario only **onCreate()** gets called

**2. Incremental-Upgrade**
when the user updates its application from old version to new version, in this scenario only **onUpgrade()** gets called

Main Idea
----
| App Version | Database Version | # of Columns |
| ------------- |:-------------:| -----:|
| 1 | 1 | 1 **(A)** |
| 2 | 2 | 2 **(A,B)** |
| 3 | 3 | 3 **(A,B,C)** |
| 4 | 4 | 4 **(A,B,C,D)** |

The main idea of this tutorial is that the user should get the appropriate number of columns as mentioned above in the table, whether the user do the fresh-install or incremental-upgrade of the app.

Different Scenarios
----

| Type                | Scenario| # of Columns |
| ------------------- |:-------:|:------------:|
| Fresh install       | 1       | 1 |
| Fresh install       | 2       | 2 |
| Fresh install       | 3       | 3 |
| Fresh install       | 4       | 4 |
| Incremental-Upgrade | 1->2    | 2 |
| Incremental-Upgrade | 1->3    | 3 |
| Incremental-Upgrade | 1->4    | 4 |
| Incremental-Upgrade | 2->3    | 3 |
| Incremental-Upgrade | 2->4    | 4 |
| Incremental-Upgrade | 3->4    | 4 |


Android App
----
All 4 Android apps are available at [Android-Applications](https://github.com/shanraisshan/Android-Database-Upgrade-Tutorial/tree/master/Android-Applications) folder.

1. DBv1
2. DBv2
3. DBv3
4. DBv4

**Apk:**

Apk is avaiable at [Shayan](https://github.com/shanraisshan/Android-Database-Upgrade-Tutorial/tree/master/Android-Applications/DBv1/Shayan) folder of each app.

**Database:**

The SQLite database of the application that is generally located at
````java
//data/data/<Your-Application-Package-Name>/databases/<your-database-name>
````
is also pulled out from internal location using [Android-Database-Viewer](https://github.com/shanraisshan/Android-Database-Viewer) class named [DatabaseUtil.java](https://github.com/shanraisshan/Android-Database-Viewer/blob/master/DatabaseUtil.java), and is saved to [Shayan](https://github.com/shanraisshan/Android-Database-Upgrade-Tutorial/tree/master/Android-Applications/DBv1/Shayan) folder of each app.
