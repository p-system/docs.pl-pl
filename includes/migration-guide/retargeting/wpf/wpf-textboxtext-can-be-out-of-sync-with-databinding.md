### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="31276-101">WPF TextBox.Text mogą być poza synchronizacja z wiązania danych</span><span class="sxs-lookup"><span data-stu-id="31276-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="31276-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="31276-102">Details</span></span>|<span data-ttu-id="31276-103">W niektórych przypadkach <xref:System.Windows.Controls.TextBox.Text> właściwość odzwierciedla poprzedniej wartości wartości właściwości z danymi, jeśli właściwość jest modyfikowany podczas wiązania z danymi operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="31276-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="31276-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="31276-104">Suggestion</span></span>|<span data-ttu-id="31276-105">Nie powinno to mieć żadnego negatywnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="31276-105">This should have no negative impact.</span></span> <span data-ttu-id="31276-106">Jednak można przywrócić poprzednie ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> właściwości <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="31276-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="31276-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="31276-107">Scope</span></span>|<span data-ttu-id="31276-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="31276-108">Edge</span></span>|
|<span data-ttu-id="31276-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="31276-109">Version</span></span>|<span data-ttu-id="31276-110">4.5</span><span class="sxs-lookup"><span data-stu-id="31276-110">4.5</span></span>|
|<span data-ttu-id="31276-111">Typ</span><span class="sxs-lookup"><span data-stu-id="31276-111">Type</span></span>|<span data-ttu-id="31276-112">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="31276-112">Retargeting</span></span>|
|<span data-ttu-id="31276-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="31276-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
