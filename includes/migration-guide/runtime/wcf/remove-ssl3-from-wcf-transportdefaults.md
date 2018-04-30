### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="e12d8-101">Usuń Ssl3 z WCF TransportDefaults</span><span class="sxs-lookup"><span data-stu-id="e12d8-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e12d8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e12d8-102">Details</span></span>|<span data-ttu-id="e12d8-103">Używając NetTcp z zabezpieczeniami transportu i typu poświadczeń certyfikatu protokołu SSL 3 nie jest już domyślnym protokołem używane do negocjowania bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="e12d8-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="e12d8-104">W większości przypadków należy bez wpływu na istniejące aplikacje jako protokołu TLS 1.0 ma zawsze uwzględnionych na liście protokół dla NetTcp.</span><span class="sxs-lookup"><span data-stu-id="e12d8-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="e12d8-105">Wszyscy istniejący klienci powinno być możliwe do negocjowania połączenia przy użyciu na co najmniej TLS1.0.</span><span class="sxs-lookup"><span data-stu-id="e12d8-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>|
|<span data-ttu-id="e12d8-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e12d8-106">Suggestion</span></span>|<span data-ttu-id="e12d8-107">Jeśli wymagana jest Ssl3, użyj jednej z następujących mechanizmów konfiguracji do dodania do listy protokołów wynegocjowanym Ssl3.</span><span class="sxs-lookup"><span data-stu-id="e12d8-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="e12d8-108">[&lt;sslStreamSecurity&gt; sekcji &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="e12d8-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>|
|<span data-ttu-id="e12d8-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="e12d8-109">Scope</span></span>|<span data-ttu-id="e12d8-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="e12d8-110">Edge</span></span>|
|<span data-ttu-id="e12d8-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="e12d8-111">Version</span></span>|<span data-ttu-id="e12d8-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e12d8-112">4.6.2</span></span>|
|<span data-ttu-id="e12d8-113">Typ</span><span class="sxs-lookup"><span data-stu-id="e12d8-113">Type</span></span>|<span data-ttu-id="e12d8-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e12d8-114">Runtime</span></span>|
|<span data-ttu-id="e12d8-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e12d8-115">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
