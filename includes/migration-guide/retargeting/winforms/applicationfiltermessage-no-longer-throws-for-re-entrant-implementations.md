### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage już zgłasza wielobieżnej implementacji IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Szczegóły|Przed .NET Framework 4.6.1, wywoływania <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> z <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> której wywołać <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> lub <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (podczas wywoływania również <xref:System.Windows.Forms.Application.DoEvents>) spowodowałoby <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, to nie jest już wyjątku i filtry wielobieżnej zgodnie z powyższym opisem mogą być używane.|
|Sugestia|Należy pamiętać, że <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> nie zgłosi wyjątku dla wielobieżnej <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> zachowanie opisane powyżej. Dotyczy to tylko aplikacji .NET Framework 4.6.1.Apps przeznaczonych dla platformy .NET Framework 4.6.1 można zrezygnować z tej zmiany (lub zrezygnować struktur starszych docelowych w aplikacji) przy użyciu [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) zgodność przełącznika.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

