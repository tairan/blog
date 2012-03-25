---
layout: post
title: 使用SC创建/删除Windows Services
tags:
- SC
- Technology
- 我的声音
status: publish
type: post
published: true
meta:
  _searchme: '1'
  blogger_blog: hackersstory.blogspot.com
  blogger_author: Hacker Wanghttp://www.blogger.com/profile/09490459533264275905noreply@blogger.com
  blogger_permalink: /2008/06/scwindows-services.html
  aktt_notify_twitter: 'no'
  _edit_last: '2'
---
DESCRIPTION:<br />        SC is a command line program used for communicating with the<br />        Service Control Manager and services.<br />USAGE:<br />        sc  [command] [service name]  ...<br /><br /><br />        The option  has the form "ServerName"<br />        Further help on commands can be obtained by typing: "sc [command]"<br />        Commands:<br />          query-----------Queries the status for a service, or<br />                          enumerates the status for types of services.<br />          queryex---------Queries the extended status for a service, or<br />                          enumerates the status for types of services.<br />          start-----------Starts a service.<br />          pause-----------Sends a PAUSE control request to a service.<br />          interrogate-----Sends an INTERROGATE control request to a service.<br />          continue--------Sends a CONTINUE control request to a service.<br />          stop------------Sends a STOP request to a service.<br />          config----------Changes the configuration of a service (persistent).<br />          description-----Changes the description of a service.<br />          failure---------Changes the actions taken by a service upon failure.<br />          failureflag-----Changes the failure actions flag of a service.<br />          sidtype---------Changes the service SID type of a service.<br />          privs-----------Changes the required privileges of a service.<br />          qc--------------Queries the configuration information for a service.<br />          qdescription----Queries the description for a service.<br />          qfailure--------Queries the actions taken by a service upon failure.<br />          qfailureflag----Queries the failure actions flag of a service.<br />          qsidtype--------Queries the service SID type of a service.<br />          qprivs----------Queries the required privileges of a service.<br />          delete----------Deletes a service (from the registry).<br />          create----------Creates a service. (adds it to the registry).<br />          control---------Sends a control to a service.<br />          sdshow----------Displays a service's security descriptor.<br />          sdset-----------Sets a service's security descriptor.<br />          showsid---------Displays the service SID string corresponding to an arbitrary name.<br />          GetDisplayName--Gets the DisplayName for a service.<br />          GetKeyName------Gets the ServiceKeyName for a service.<br />          EnumDepend------Enumerates Service Dependencies.<br /><br />        The following commands don't require a service name:<br />        sc   <br />          boot------------(ok | bad) Indicates whether the last boot should<br />                          be saved as the last-known-good boot configuration<br />          Lock------------Locks the Service Database<br />          QueryLock-------Queries the LockStatus for the SCManager Database<br />EXAMPLE:<br />        sc start MyService
