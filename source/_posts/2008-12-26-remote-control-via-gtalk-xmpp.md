---
layout: post
title: Remote Control via GTalk (XMPP)
tags:
- GTalk
- Remote Control
- Technology
- XMPP
- 我的声音
status: publish
type: post
published: true
meta:
  _edit_last: '2'
  aktt_notify_twitter: 'no'
---
想远程控制家里的电脑？却因IP地址动态分配(花生壳可以解决)，远程连接速度慢，机器暴露在外网怕不安全，等种种原因无法理想的实现。

现在我们就另辟蹊径使用Gtalk来远程控制家里的电脑

基本思路如下
Gtalk基于XMPP这个开放的协议。那么我们也基于XMPP协议开发一个客户端就可以和Gtalk进行通讯，可以发送和接收来自Gtalk的消息后，再进行扩展，做成一个shell(命令解释器)。当我们用Gtalk给客户端发送消息后，客户端接收消息进行解释并处理。这样就完成了远程控制的家里电脑的任务。

具体实现
本人才采用的是.NET技术，使用agsXMPP这个开源的封装了XMPP协议的类库。我们基于这个类库就可以和Gtalk通讯了。
下面附上源码，这里只是实现使用Gtalk发送消息，客户端接收到消息后自动将接收的消息再发送回去。

<pre lang="csharp">
using System;

using agsXMPP;
using agsXMPP.protocol.client;

namespace XMPPClient
{
    class Program
    {
        static void Main(string[] args)
        {
            XmppClientConnection xmpp = new XmppClientConnection();

            xmpp.Server = "gmail.com";
            xmpp.Username = "your_username";
            xmpp.Password = "your_password";
            xmpp.ConnectServer = "talk.google.com";
            xmpp.SocketConnectionType = agsXMPP.net.SocketConnectionType.Direct;
            xmpp.ClientVersion = "1.0";
            xmpp.AutoRoster = true;

            xmpp.Open();

            Console.WriteLine("connected.");

            xmpp.Show = agsXMPP.protocol.client.ShowType.away;
            xmpp.OnLogin += new ObjectHandler(xmpp_OnLogin);
            xmpp.OnMessage += new MessageHandler(xmpp_OnMessage);

            Console.ReadKey();
        }

        static void xmpp_OnRosterItem(object sender, agsXMPP.protocol.iq.roster.RosterItem item)
        {
            Console.WriteLine(string.Format("{0} was found", item.Jid));
        }

        static void xmpp_OnMessage(object sender, agsXMPP.protocol.client.Message msg)
        {
            Message response = new Message();
            response.To = msg.From;
            response.Type = MessageType.chat;
            response.Body = string.Format("{0}", msg.Body);
            //replay
            (sender as XmppClientConnection).Send(response);
        }

        static void xmpp_OnLogin(object sender)
        {
            Console.WriteLine(string.Format("{0} login.", (sender as XmppClientConnection).Username));
        }
    }
}
</pre>

后面的工作就是扩展了，既然能够接收到消息，那么再实现一个消息解释器就可以根据发送过来的消息来做一些事情了。理论上我们能控制这台机器上的所有资源！

Note:
这个想法源自同事(老江)的灵感，他现在正基于此实现远程控制家中的电脑用BT，电驴等方式下载电影，只是他还要把WCF掺和进来一起玩，所以做的比较复杂。我这里化繁为简，只是实现一个可扩展的Shell也是要一番功夫的。
