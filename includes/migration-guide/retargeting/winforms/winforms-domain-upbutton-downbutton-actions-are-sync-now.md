### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="f3ced-101">Akcje upbutton i downbutton domeny w kontrolce są teraz zsynchronizowane</span><span class="sxs-lookup"><span data-stu-id="f3ced-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f3ced-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f3ced-102">Details</span></span>|<span data-ttu-id="f3ced-103">W poprzednich wersjach i .NET Framework 4.7.1 <xref:System.Windows.Forms.DomainUpDown> formantu <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji jest ignorowana, gdy tekst formantu jest obecny i dewelopera jest wymagany do użycia <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcji w formancie przed użyciem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji.</span><span class="sxs-lookup"><span data-stu-id="f3ced-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="f3ced-104">Począwszy od programu .NET Framework 4.7.2 zarówno <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcje pracować wielel osób, w tym scenariuszu i pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="f3ced-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>|
|<span data-ttu-id="f3ced-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f3ced-105">Suggestion</span></span>|<span data-ttu-id="f3ced-106">Aby dla aplikacji, aby korzystać z tych zmian, należy uruchomić w programie .NET Framework 4.7.2 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="f3ced-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="f3ced-107">Aplikacji mogą korzystać z tych zmian w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="f3ced-107">The application can benefit from these changes in either of the following ways:</span></span><ul><li><span data-ttu-id="f3ced-108">Jest ponownie kompilowana docelową programu .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="f3ced-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="f3ced-109">Ta zmiana jest domyślnie włączona w aplikacji formularzy systemu Windows, które odnoszą się do programu .NET Framework 4.7.2 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f3ced-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span></li><li><span data-ttu-id="f3ced-110">Zdecyduje się poza starsza przewijanie zachowanie przez dodanie poniższego [przełącznika AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracji aplikacji i ustawieniem dla niego <code>false</code>, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f3ced-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>, as the following example shows.</span></span></li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="f3ced-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="f3ced-111">Scope</span></span>|<span data-ttu-id="f3ced-112">Krawędź</span><span class="sxs-lookup"><span data-stu-id="f3ced-112">Edge</span></span>|
|<span data-ttu-id="f3ced-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="f3ced-113">Version</span></span>|<span data-ttu-id="f3ced-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f3ced-114">4.7.2</span></span>|
|<span data-ttu-id="f3ced-115">Typ</span><span class="sxs-lookup"><span data-stu-id="f3ced-115">Type</span></span>|<span data-ttu-id="f3ced-116">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="f3ced-116">Retargeting</span></span>|
|<span data-ttu-id="f3ced-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f3ced-117">Affected APIs</span></span>|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|
