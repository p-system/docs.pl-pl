### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="f3c41-101">Fokus klawiatury teraz porusza się prawidłowo na wielu warstw hosting WinForms/WPF</span><span class="sxs-lookup"><span data-stu-id="f3c41-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f3c41-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f3c41-102">Details</span></span>|<span data-ttu-id="f3c41-103">Należy wziąć pod uwagę formant programu WinForms, który z kolei obsługuje formantów WPF hosting aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="f3c41-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="f3c41-104">Użytkownicy nie mogą mieć możliwość karcie poza warstwą WinForms, jeśli formant pierwszego lub ostatniego w tej warstwie jest WPF <code>System.Windows.Forms.Integration.ElementHost</code>.</span><span class="sxs-lookup"><span data-stu-id="f3c41-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF <code>System.Windows.Forms.Integration.ElementHost</code>.</span></span> <span data-ttu-id="f3c41-105">Ta zmiana rozwiązuje ten problem, a użytkownicy mogą teraz karcie poza warstwą WinForms. Automatyczne aplikacje, które są oparte na fokus nigdy nie anulowanie warstwy WinForms może przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f3c41-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>|
|<span data-ttu-id="f3c41-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f3c41-106">Suggestion</span></span>|<span data-ttu-id="f3c41-107">Deweloper, który chce korzystać z tej zmiany podczas określania wartości docelowej wersji struktury poniżej .NET 4.7.2 można ustawić następujący zestaw AppContext flagi na wartość false, aby zmiana można włączyć.</span><span class="sxs-lookup"><span data-stu-id="f3c41-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="f3c41-108">Aplikacje WPF musi zgłosić się do wszystkich wczesne ulepszenia ułatwień dostępu, aby uzyskać nowsze ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="f3c41-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="f3c41-109">Innymi słowy, zarówno <code>Switch.UseLegacyAccessibilityFeatures</code> i <code>Switch.UseLegacyAccessibilityFeatures.2</code> przełączniki muszą być setA projektanta, który wymaga poprzedniej funkcji podczas określania wartości docelowej .NET 4.7.2 lub większa może ustawione następujące flagi AppContext na wartość true zmiany, które mają zostać wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f3c41-109">In other words, both the <code>Switch.UseLegacyAccessibilityFeatures</code> and the <code>Switch.UseLegacyAccessibilityFeatures.2</code> switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="f3c41-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="f3c41-110">Scope</span></span>|<span data-ttu-id="f3c41-111">Krawędź</span><span class="sxs-lookup"><span data-stu-id="f3c41-111">Edge</span></span>|
|<span data-ttu-id="f3c41-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="f3c41-112">Version</span></span>|<span data-ttu-id="f3c41-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f3c41-113">4.7.2</span></span>|
|<span data-ttu-id="f3c41-114">Typ</span><span class="sxs-lookup"><span data-stu-id="f3c41-114">Type</span></span>|<span data-ttu-id="f3c41-115">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="f3c41-115">Retargeting</span></span>|
