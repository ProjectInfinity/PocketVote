PocketMine Plugin Documentation
===============================

This file is continuously updated. If you feel something is missing or
incorrect, please open an issue.

Commands
========

| Command   | Permission      | Description                                                 |
|-----------|-----------------|-------------------------------------------------------------|
| /vote     | pocketvote.vote | Shows the MCPE.guru voting link associated with the server. |
| /vote top | pocketvote.vote | Shows the top voters the past month.                        |

Configuration
=============

| Key                         | Description                                                                                                                                                                                                                                                |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| version                     | Used to track how the configuration should be altered in order to be completely up to date.                                                                                                                                                                |
| identity                    | The identity given to you from [PocketVote.io](https://pocketvote.io) which is used to identify your server.                                                                                                                                               |
| secret                      | The secret given to you from [PocketVote.io](https://pocketvote.io) which is given to voting sites.                                                                                                                                                        |
| lock                        | If set to true, the commands to alter secret or identity is disabled.                                                                                                                                                                                      |
| vote-expiration             | An amount of time to keep votes that have not been redeemed by a player, specified in **days**.                                                                                                                                                            |
| multi-server.enabled        | If set to true, PocketVote will allow you to sync votes across multiple servers by using MySQL as the backend.                                                                                                                                             |
| multi-server.role           | If set to ‘master’ the server will talk to the PocketVote servers and store voting information in the MySQL database. If set to ‘slave’ the server will not talk to the PocketVote servers but instead check the specified MySQL server for pending votes. |
| multi-server.mysql.host     | The hostname of your MySQL server.                                                                                                                                                                                                                         |
| multi-server.mysql.port     | The port of your MySQL server.                                                                                                                                                                                                                             |
| multi-server.mysql.username | The username of your MySQL server.                                                                                                                                                                                                                         |
| multi-server.mysql.password | The password of your MySQL server.                                                                                                                                                                                                                         |
| multi-server.mysql.database | The database name of your MySQL server.                                                                                                                                                                                                                    |
| onvote.run-cmd              | A list of commands that are to be ran immediately as a vote is retrieved. The following variables can be used in the commands: %player, %site, %ip.                                                                                                        |
| onvote.online-cmd           | A list of commands that are to be ran as soon as the target player is online. The following variables can be used in the commands: %player, %site, %ip.                                                                                                    |
| votes                       | A list of votes waiting for players to log on. Please leave this alone.                                                                                                                                                                                    |
