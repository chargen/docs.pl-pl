# [Programowanie dla sieci w programie .NET Framework](index.md)
## [Programowanie dla sieci — tematy z instrukcjami](network-programming-how-to-topics.md)
## [Wprowadzenie protokołów podłączanych](introducing-pluggable-protocols.md)
## [Żądanie danych](requesting-data.md)
### [Tworzenie żądań internetowych](creating-internet-requests.md)
### [Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
### [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
### [Instrukcje: przesyłanie danych przy użyciu klasy WebRequest](how-to-send-data-using-the-webrequest-class.md)
### [Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
### [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
### [Tworzenie żądań asynchronicznych](making-asynchronous-requests.md)
### [Obsługa błędów](handling-errors.md)
## [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
### [Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest](how-to-register-a-custom-protocol-using-webrequest.md)
### [Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
### [Wyprowadzanie z elementu WebRequest](deriving-from-webrequest.md)
### [Wyprowadzanie z elementu WebResponse](deriving-from-webresponse.md)
## [Korzystanie z protokołów aplikacji](using-application-protocols.md)
### [HTTP](http.md)
#### [HttpListener](httplistener.md)
### [Instrukcje: dostęp do właściwości specyficznych dla protokołu HTTP](how-to-access-http-specific-properties.md)
### [Zarządzanie połączeniami](managing-connections.md)
#### [Grupowanie połączeń](connection-grouping.md)
#### [Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych](how-to-assign-user-information-to-group-connections.md)
### [TCP-UDP](tcp-udp.md)
#### [Stosowanie usług TCP](using-tcp-services.md)
#### [Stosowanie usług UDP](using-udp-services.md)
### [Gniazda](sockets.md)
#### [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)
#### [Używanie gniazd klientów](using-client-sockets.md)
##### [Używanie synchronicznego gniazda klienta](using-a-synchronous-client-socket.md)
##### [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
#### [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
##### [Używanie synchronicznego gniazda serwera](using-a-synchronous-server-socket.md)
##### [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
#### [Przykłady kodu gniazd](socket-code-examples.md)
##### [Przykład synchronicznego gniazda klienta](synchronous-client-socket-example.md)
##### [Przykład synchronicznego gniazda serwera](synchronous-server-socket-example.md)
##### [Przykład asynchronicznego gniazda klienta](asynchronous-client-socket-example.md)
##### [Przykład asynchronicznego gniazda serwera](asynchronous-server-socket-example.md)
### [FTP](ftp.md)
#### [Instrukcje: pobieranie plików przy użyciu protokołu FTP](how-to-download-files-with-ftp.md)
#### [Instrukcje: przekazywanie plików przy użyciu protokołu FTP](how-to-upload-files-with-ftp.md)
#### [Instrukcje: wyświetlanie zawartości katalogu przy użyciu protokołu FTP](how-to-list-directory-contents-with-ftp.md)
### [Opis problemów i wyjątków dotyczących elementów WebRequest](understanding-webrequest-problems-and-exceptions.md)
## [Protokół IPv6](internet-protocol-version-6.md)
### [Adresowanie IPv6](ipv6-addressing.md)
### [Routing IPv6](ipv6-routing.md)
### [Automatyczna konfiguracja IPv6](ipv6-auto-configuration.md)
### [Włączanie i wyłączanie protokołu IPv6](enabling-and-disabling-ipv6.md)
### [Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)
## [Konfigurowanie aplikacji internetowych](configuring-internet-applications.md)
## [Śledzenie sieci w programie .NET Framework](network-tracing.md)
### [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
### [Włączanie śledzenia sieci](enabling-network-tracing.md)
### [Instrukcje: konfigurowanie śledzenia sieci](how-to-configure-network-tracing.md)
## [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
### [Zasady pamięci podręcznej](cache-policy.md)
### [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
### [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
#### [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
#### [Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
### [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
#### [Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji](how-to-set-a-location-based-cache-policy-for-an-application.md)
#### [Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji](how-to-set-the-default-time-based-cache-policy-for-an-application.md)
#### [Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu](how-to-customize-a-time-based-cache-policy.md)
#### [Instrukcje: ustawianie zasad pamięci podręcznej dla żądania](how-to-set-cache-policy-for-a-request.md)
## [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
### [Najlepsze rozwiązania dotyczące protokołu Transport Layer Security (TLS)](tls.md)
### [Używanie protokołu Secure Sockets Layer](using-secure-sockets-layer.md)
#### [Wybór i sprawdzanie poprawności certyfikatu](certificate-selection-and-validation.md)
### [Uwierzytelnianie internetowe](internet-authentication.md)
#### [Uwierzytelnianie podstawowe i szyfrowane](basic-and-digest-authentication.md)
#### [Uwierzytelnianie NTLM i uwierzytelnianie Kerberos](ntlm-and-kerberos-authentication.md)
### [Internet i uprawnienia gniazd](web-and-socket-permissions.md)
## [Najlepsze rozwiązania dotyczące klas System.Net](best-practices-for-system-net-classes.md)
## [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
### [Konfiguracja serwera proxy](proxy-configuration.md)
### [Automatyczne wykrywanie serwera proxy](automatic-proxy-detection.md)
### [Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest](how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet.md)
### [Instrukcje: zastępowanie wyboru globalnego serwera proxy](how-to-override-a-global-proxy-selection.md)
## [NetworkInformation](networkinformation.md)
### [Instrukcje: wykrywanie dostępności sieci i zmian adresów](how-to-detect-network-availability-and-address-changes.md)
### [Instrukcje: uzyskiwanie informacji o interfejsie i protokole](how-to-get-interface-and-protocol-information.md)
### [Instrukcje: polecenie ping do hosta](how-to-ping-a-host.md)
## [Zmiany w przestrzeni nazw System.Uri w wersji 2.0](changes-to-the-system-uri-namespace-in-version-2-0.md)
## [Obsługa identyfikatorów zasobów międzynarodowych w System.Uri](international-resource-identifier-support-in-system-uri.md)
## [Ulepszenia wydajności gniazda w wersji 3.5](socket-performance-enhancements-in-version-3-5.md)
## [Protokół PNRP](peer-name-resolution-protocol.md)
### [Nazwy elementów równorzędnych i identyfikatory PNRP](peer-names-and-pnrp-ids.md)
### [Publikowanie i rozwiązywanie nazw elementów równorzędnych](peer-name-publication-and-resolution.md)
### [Chmury PNRP](pnrp-clouds.md)
### [Pamięci podręczne PNRP](pnrp-caches.md)
### [PNRP w projektowaniu aplikacji](pnrp-in-application-development.md)
## [Współpraca równorzędna](peer-to-peer-collaboration.md)
### [Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje](about-the-system-net-peertopeer-collaboration-namespace.md)
### [Scenariusze sieci równorzędnych](peer-to-peer-networking-scenarios.md)
## [Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)
## [Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną](integrated-windows-authentication-with-extended-protection.md)
## [Przechodzenie translatora adresów sieciowych przy użyciu protokołu IPv6 i Teredo](nat-traversal-using-ipv6-and-teredo.md)
## [Izolacja sieci dla aplikacji ze sklepu Windows Store](network-isolation-for-windows-store-apps.md)
## [Przykłady programowania sieciowego](network-programming-samples.md)
