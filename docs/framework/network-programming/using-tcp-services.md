---
title: "Za pomocą usług TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f560ae08c928e9f21def9f69950efbd72ccb6b88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-tcp-services"></a><span data-ttu-id="414b0-102">Za pomocą usług TCP</span><span class="sxs-lookup"><span data-stu-id="414b0-102">Using TCP Services</span></span>
<span data-ttu-id="414b0-103"><xref:System.Net.Sockets.TcpClient> Klasy żąda danych od zasobu internetowego za pomocą protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="414b0-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="414b0-104">Metody i właściwości **TcpClient** abstrakcyjnej szczegółowe informacje dotyczące tworzenia <xref:System.Net.Sockets.Socket> żądania i odbierania danych za pomocą protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="414b0-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="414b0-105">Ponieważ połączenie z urządzeniem zdalnym jest reprezentowana jako strumienia, dane można Odczyt i zapis techniki obsługi strumienia .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="414b0-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>  
  
 <span data-ttu-id="414b0-106">Protokół TCP ustanawia połączenie ze zdalnego punktu końcowego, a następnie używa tego połączenia w celu wysyłania i odbierania pakietów danych.</span><span class="sxs-lookup"><span data-stu-id="414b0-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="414b0-107">Protokół TCP jest odpowiedzialny za zapewnienie, że pakiety danych są wysyłane do punktu końcowego i zebranych w odpowiedniej kolejności, po ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="414b0-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>  
  
 <span data-ttu-id="414b0-108">Nawiązywania połączeń TCP, musisz znać adres urządzenia sieciowego obsługującego usługę, które są potrzebne, i musi znać port TCP używany przez usługę do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="414b0-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="414b0-109">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (zobacz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="414b0-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="414b0-110">Usługi nie ma na liście przez organizację Iana może mieć numeru portu z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="414b0-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="414b0-111">W poniższym przykładzie pokazano ustawienie się **TcpClient** nawiązać połączenia z serwerem czasu na porcie TCP 13.</span><span class="sxs-lookup"><span data-stu-id="414b0-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="414b0-112"><xref:System.Net.Sockets.TcpListener>Służy do monitorowania port TCP dla żądań przychodzących, a następnie utworzyć albo **gniazda** lub **TcpClient** który zarządza połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="414b0-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="414b0-113"><xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umożliwia nasłuchiwania i <xref:System.Net.Sockets.TcpListener.Stop%2A> metody wyłącza nasłuchiwanie na porcie.</span><span class="sxs-lookup"><span data-stu-id="414b0-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="414b0-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda akceptuje przychodzące żądania połączeń i tworzy **TcpClient** można obsłużyć żądania i <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda akceptuje przychodzące żądania połączeń i tworzy **gniazda**obsłużyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="414b0-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>  
  
 <span data-ttu-id="414b0-115">W poniższym przykładzie pokazano tworzenie sieci czas serwera za pomocą **TcpListener** monitorować TCP port 13.</span><span class="sxs-lookup"><span data-stu-id="414b0-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="414b0-116">Po zaakceptowaniu przychodzącego żądania połączenia czas server odpowie bieżącą datę i godzinę z serwera hosta.</span><span class="sxs-lookup"><span data-stu-id="414b0-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="414b0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="414b0-117">See Also</span></span>  
 