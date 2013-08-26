Oozie R helper,
============================

The data science team wanted to be able to run R script using oozie, 

They wanted to be able to run ETL using Hive and on the result of that ETL they wanted to run the r script.

So I created a bash script that take 3 arguments:
1. The HDFS input of the files they want to run
2. The R script they want to run
3. The output on the hdfs where they want their result to be. (currentlt because the user is mapred I allow only /tmp/)

How to run
==========
You can use a shell oozie action like this:

<shell xmlns="uri:oozie:shell-action:0.1">
            <job-tracker>${jobTracker}</job-tracker>
            <name-node>${nameNode}</name-node>
            <exec>run_r_hadoop.sh</exec>
              <argument>/user/hive/warehouse/dual</argument>
              <argument>count.r</argument>
              <argument>/tmp/r_test</argument>
            <file>count.r#count.r</file>
</shell>


Prequesite
==========
R and all its libraries should be installe on all Hadoop salves, including all the libraries that are used

