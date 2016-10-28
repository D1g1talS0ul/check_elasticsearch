Nagios check script for elasticsearch
=====================================

This is a simple script to check the status of an elasticsearch cluster.

Usage:

    ./check_elasticsearch -H es1.mysite.com -P 9200 -o /tmp

This will output the standard Nagios format:

    OK - elasticsearch (cluster) is running. status: green; timed_out: false; number_of_nodes: 3; number_of_data_nodes: 2; active_primary_shards: 241; active_shards: 482 100.0; relocating_shards: 0; initializing_shards: 0; unassigned_shards: 0 0; delayed_unassigned_shards: 0; number_of_pending_tasks: 0; number_of_in_flight_fetch: 0; task_max_waiting_in_queue_millis: 0; active_shards_percent_as_number: 100.0  | 'active_primary'=241 'active'=482 100.0 'relocating'=0 'init'=0 'unass'=0


`OK` / `WARNING` / `CRITICAL` correspond to the status being "green", "yellow", or "red" respectively.

If you have a Graphite server you can send data to it via:

    ./check_elasticsearch -H es1.mysite.com -P 9200 -c graphite.foo.com -C 2003
    
This will output data to the following metric prefix:

    system.$cluster_name.cluster.app.elasticsearch.cluster
    
If you use [Chef](https://www.getchef.com/chef/) there is a cookbook for installing this plugin at [https://github.com/cjs226/check_elasticsearch_cookbook](https://github.com/cjs226/check_elasticsearch_cookbook).

Script is a modified version of check\_phpfpm by [MAB](https://github.com/mabitt/mab-nagios-plugins).

Enjoy.
