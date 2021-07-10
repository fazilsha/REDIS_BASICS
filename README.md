# REDIS_BASICS
### -INTRODUCTION-
  * open source, BSD licensed, advanced key-value store
  * referred to as a data structure server, since the keys can contain strings, hashes, lists, sets and sorted sets
  * written in C
  * create and deploy a highly scalable and performance-oriented system.
### -PRE-REQUISTES-
  * Basic knowledge of Data structure
### -THREE MAIN PECULIARITIES-
  * Holds its database entirely in the memory, using the disk only for persistence.
  * Relatively rich set of data types when compared to many key-value data stores.
  * Replicate data to any number of slaves.
### -ADVANTAGES-
  * Exceptionally fast
  * Supports rich data types
  * Operations are atomic [two clients concurrently access, Redis server will receive the updated value.]
  * Multi-utility tool [caching, messaging-queues (Redis natively supports Publish/Subscribe), any short-lived data in your application, such as web application sessions, web page hit counts, etc.]

# SETTING UP REDIS ENVIRONMENT IN KALI LINUX
### -INSTALLING REDIS-
  * $sudo apt-get update 
  * $sudo apt-get install redis-server
### -STARTING REDIS-
  * $redis-server
  * After hitting above command,open new terminal. Note: Don't close the terminal which we used to run $redis-server command
  * ^START OVER CHECK^
    - $redis-cli 
    - You will see something like this[ redis 127.0.0.1:6379>]
    - Server is running on your local machine. To check for successful connection..Hit ping command. You should get a reply as "PONG".Then you re all set to go.
    - redis 127.0.0.1:6379> ping 
      - PONG
# CONFIGURING REDIS 
### -redis.conf-
  * (redis.conf) available at the root directory of Redis. Although you can get and set all Redis configurations by Redis CONFIG command 
  * $ CONFIG GET CONFIG_SETTING_NAME
  * ### EXAMPLE:
    - redis 127.0.0.1:6379> CONFIG GET loglevel 
  * ### To list all the available commands
    - 127.0.0.1:6379> CONFIG GET *
    - You can get the list like below.
    - I got 302 entries,Some are suppressed for demo purpose.
  1) "rdbchecksum"
  2) "yes"
  3) "daemonize"
  4) "no"
  5) "io-threads-do-reads"
  6)  .....
  302) "0 200 800"
### EDIT CONFIGURATION
   * To update configuration, you can edit redis.conf file directly or you can update configurations via CONFIG set command.
   * ### BASIC SYNTAX FOR CONFIG SET
   * redis 127.0.0.1:6379> CONFIG SET CONFIG_SETTING_NAME NEW_CONFIG_VALUE
   * EXAMPLE:
     - redis 127.0.0.1:6379> CONFIG SET loglevel "notice" 
     - OK 
     - redis 127.0.0.1:6379> CONFIG GET loglevel  
     - 1) "loglevel" 
     - 2) "notice"
### DATA TYPES
* Redis supports 5 types of data types.
  - Strings
  - Hashes
  - Lists
  - Sets
  - Sorted sets
  ### Strings
    - Redis string is a sequence of bytes
    - Strings in Redis are binary safe, meaning they have a known length not determined by any special terminating characters.
    - Thus, you can store anything up to 512 megabytes in one string.
    * Example:
      - 127.0.0.1:6379> SET name "Networkx011"
      - OK
      - 127.0.0.1:6379> GET name
      - "Networkx011"
      - 127.0.0.1:6379>
     * SET and GET are the redis command used.
     * name ---> name is the key which has the value "Networkx011"
     * To set the value we re using SET KEY_NAME STRING_VALUE
     * To retrieve back, use GET KEY_NAME
  ### Hashes
     * A Redis hash is a collection of key value pairs.
     * Redis Hashes are maps between string fields and string values.
     * Hence, they are used to represent objects.
     * EXAMPLE:
       - 127.0.0.1:6379> HMSET user:1 networkx011 newyork phone +19973673723
       - OK
       - 127.0.0.1:6379> HGETALL USER:1
       - (empty array)
       - 127.0.0.1:6379> HGETALL user:1
       - 1) "networkx011"
       - 2) "newyork"
       - 3) "phone"
       - 4) "+19973673723"
     * Hash data type is used to store the user's object which contains basic information of the user.
     * Here HMSET, HGETALL are commands for Redis, while user − 1 is the key.
     * Every hash can store up to 232 - 1 field-value pairs (more than 4 billion).
