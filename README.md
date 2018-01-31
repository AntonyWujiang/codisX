<img src="doc/pictures/logo-3.png" height=80></img>

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/CodisLabs/codis?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/CodisLabs/codis.svg)](https://travis-ci.org/CodisLabs/codis)

Codis is a proxy based high performance Redis cluster solution written in Go, which is widely used in many companies.
CodisX is based on the latest version of codis 3.2.2.

As is known, in production scenarios, we basically use cache in two ways:
1. key-value database, which requires high consistency
2. pure cache, only for the purpose of accelerating data access. In this case, slave servers are not necessary any more. We should use as many master servers as possible.

Thus, I've made some changes to official codis 3.2.2. Now, you can edit dashboard.conf to change the working mode of codis(only accept 'CP' & 'AP'), and edit proxy.conf to change the retry times of requests in case of server failure.

In CP mode, codisX is just the same as codis 3.2.2.
While in AP mode, you are supposed to edit weights of each group. When one group fails over, requests will be sent to the next server based on Consistent hash algorithm, which ensures high accessibility to adapt to pure cache scenario.

Besides, if the feature of replica groups is enabled, read requests will only be sent to slaves.

If you have questions on codisX, feel free to send e-mails to me (e0012443@u.nus.edu).

## Architecture

![architecture](doc/pictures/architecture.png)

## Snapshots

GroupWeights
![groupWeights](doc/pictures/group_weights.png)

## official address of codis
https://github.com/CodisLabs/codis
