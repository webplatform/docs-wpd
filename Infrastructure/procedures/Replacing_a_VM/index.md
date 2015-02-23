{{:WPD:Infrastructure/architecture}}
= Replacing a VM =

This document will describe how you can replace any VM in an existing deployment (e.g. production) with a new one.

This kind of action is most useful when we feel a VM has been compromised, or broken. Every VM, including the salt master, is designed to be replaceable parts of a cluster.

'''Note'''; the output of the commands shown here were done from the staging deployment level.

Get the details of one VM;

  nova list | grep app2
  | ... | app2            | ACTIVE | -          | Running     | private-network=..., 10.10.10.215, 173.236.254.224 |

We know that ''app2'' has two IP addresses assigned

* private: ''10.10.10.215''
* public: ''173.236.254.224''. If we look at the ''Fastly'' dashboard, we should have this IP in; ''docs (staging)'', ''www (staging)'', ''code (staging)'' services.

What is the flavor (i.e. Size of RAM and number of CPUs)  app2 has?

  nova show app2|grep flavor
  | flavor                               | supersonic (200)                                                       |

What ''supersonic'' has (showing only some here);

  nova flavor-list
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
  | ID  | Name       | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public | 
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+
  | 100 | subsonic   | 1024      | 80   | 0         |      | 1     | 1.0         | True      |
  | 200 | supersonic | 2048      | 80   | 0         |      | 1     | 1.0         | True      |
  | 300 | lightspeed | 4096      | 80   | 0         |      | 2     | 1.0         | True      |
  +-----+------------+-----------+------+-----------+------+-------+-------------+-----------+