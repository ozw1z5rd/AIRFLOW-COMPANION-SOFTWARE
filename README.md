# AIRFLOW-COMPANION-SOFTWARE

Got Data lake ingestion nightmares? Well, perhaps I have something that can help you.

An Airflow companion software has been designed to ingest data into the lake.

I worked for years to data lake ingestion using Airflow as workflow management software and I integrate it with a companion software which helps to manage DAGs and the status of the lake. In 3+ year of usage, not a single failure. Unfortunately, the version I wrote belongs to the company where I work, so this a completely new version which has nothing in common with the original one but some great ideas and concepts.

AIRFLOW COMPANION SOFTWARE is written in python, the same language used to write airflow and uses the same frameworks, this will make easier to change to the code.

I'm not a good front-end developer so I exposed all the function using a REST API. It starts as service, scales with no issues and relies on a solid database.

What does ACS do? A lot of things of course.

Since the data belongs to different units, after some attempts, the best practice is that they push the data into the lake as soon as they have new data available. Data in the lake don't stay forever, retention policy matters also in the lake. ACS has been written with this in mind.

  1. Tracks the status of the data. You know it: the most important part of the game is to know which data are into the lake and in which state they are. Data scientist need to know what they can use BEFORE examing the data, sometimes you have the data but it cannot be crossed with other data, to know these details helps to save time to who will use the data. ACS has a tagging system and saves a status for each data which is handled. When a DAG did not complete, it's easy to check who is impacted by this data outage.
  
  2. Centralized DAG configuration management: every DAG's configuration is handled by ACS, you can even change it in real time. The best part of ACS is that the configurations are hierarchical so you can define a parent configuration for some ingestion task, then you can inherit from this and write/overwrite only the configuration that is more specific to every single procedure. Configuration are versioned.
  
  3. Centralized resources management: how do you handle the data ingestion? The best solution is some spark procedures and mostly Hive, so you need HQL code to deduplicate, clean and order the data which reach the lake. Well, the HQL code can be changed in real time without to change the DAG code. Resources are versioned.
  
  4. DAG dependency management. ACF is able to start DAG as soon as all the data they need is available. AIRFLOW by itself allows a DAG to trigger another DAG, this is not so explicit and may lead to confusion. ACF makes these dependencies explicit and can be changed with no DAG code change.
  

AP. 19.5.2019
