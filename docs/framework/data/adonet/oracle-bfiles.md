---
title: Oracle BFILEs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f48bd85559d55d9a1190310bcf13cd4a68625011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-bfiles"></a>Oracle BFILEs
.NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z bazą danych Oracle <xref:System.Data.OracleClient.OracleType.BFile> — typ danych.  
  
 Oracle **BPLIK** ma typ danych Oracle **LOB** typ danych, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajty. Oracle **BPLIK** różni się od innych Oracle **LOB** typy danych, ponieważ jego dane są przechowywane w pliku fizycznego w systemie operacyjnym, a nie na serwerze. Należy pamiętać, że **BPLIK** — typ danych zapewnia dostęp do danych tylko do odczytu.  
  
 Inne właściwości **BPLIK** typ danych, który odróżniający go od **LOB** jego są — typ danych:  
  
-   Zawiera dane bez struktury.  
  
-   Obsługuje podziału po stronie serwera.  
  
-   Używa odwoływać się do kopiowania semantyki. Na przykład, jeśli operacja kopiowania na **BPLIK**, tylko **BPLIK** jest kopiowany Lokalizator (która jest odwołanie do pliku). Dane w pliku nie zostaną skopiowane.  
  
 **BPLIK** typ danych powinien być używany dla odwołania do obiektów LOB, które są duże, dlatego nie praktyczne mają być przechowywane w bazie danych. Uczestniczy większe obciążenie klienta, serwera i komunikację, korzystając z **BPLIK** — typ danych w porównaniu z **LOB** — typ danych. Bardziej wydajny dostęp do **BPLIK** Jeśli należy uzyskać niewielką ilość danych. Jest bardziej wydajne dostępu obiektów LOB rezydentne bazy danych, gdy trzeba uzyskać całego obiektu.  
  
 Każdy z systemem innym niż NULL **OracleBFile** obiekt jest skojarzony z dwoma obiektami, które określają lokalizację pliku fizycznego:  
  
1.  Obiekt Oracle katalogu, który jest alias bazy danych dla katalogu w systemie plików, a  
  
2.  Nazwa pliku źródłowego pliku fizycznego znajduje się w katalogu skojarzone z obiektu katalogu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# pokazano, jak utworzyć **BPLIK** w oprogramowaniu Oracle tabeli, a następnie pobrać go w formie **OracleBFile** obiektu. W przykładzie pokazano, za pomocą <xref:System.Data.OracleClient.OracleDataReader> obiektu i **OracleBFile** **wyszukiwania** i **odczytu** metody. Należy pamiętać, aby można było korzystać z tej próbki, należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" i plik o nazwie "MyFile.jpg" na serwerze programu Oracle.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)