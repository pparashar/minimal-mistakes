---
id: 519
title: 'How To: Drop, Backup and Restore a MongoDB database'
date: 2012-06-20T08:23:15+00:00
permalink: /how-to-drop-backup-and-restore-a-mongodb-database-2012-06.html
pvc_views:
  - "11804"
dsq_thread_id:
  - "733466959"
categories:
  - 'Tips, Tricks &amp; Hacks'
tags:
  - MongoDB
  - Primer
---
A quick note to self and other alike on how to drop a database, backup a database and restore a database in MongoDB.

### Drop Database

Just use the command db.dropDatabase() from the mongo command line client.

<pre>use db;
db.dropDatabase();</pre>

### Backup Database

To backup a local mongo databse Use the command line utility mongodump.

<pre>mongodump -d dbname</pre>

This would create a folder &#8220;dump&#8221; containing the dbname folder further containing all collections. Use this &#8220;dbname&#8221; folder to restore database.

### Restore Database

To restore a backup, taken earlier using mongodump, use the command mongorestore.

<pre>mongorestore -d dbname <em>Path_of_dump_folder</em></pre>

Where path of dump folder would be path till &#8220;dbname&#8221; folder from the mongodump example above.

For More detailed reference documentation on the subject, refer to the mongoDB documentation <a href="http://docs.mongodb.org/manual/administration/backups/" target="_blank">here</a> and <a href="http://www.mongodb.org/display/DOCS/Import+Export+Tools" target="_blank">here</a>  .
