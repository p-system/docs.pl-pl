### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="f6637-101">Awarii w selektora podczas usuwania elementu z kolekcji niestandardowej INCC</span><span class="sxs-lookup"><span data-stu-id="f6637-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f6637-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f6637-102">Details</span></span>|<span data-ttu-id="f6637-103"><code>T:System.InvalidOperationException</code> Może wystąpić w następującym scenariuszu:</span><span class="sxs-lookup"><span data-stu-id="f6637-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="f6637-104">Właściwość ItemsSource <code>T:System.Windows.Controls.Primitives.Selector</code> to kolekcja niestandardowych implementacji <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span><span class="sxs-lookup"><span data-stu-id="f6637-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="f6637-105">Wybrany element został usunięty z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f6637-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="f6637-106"><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Ma <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (wskazującą nieznanej pozycji).</span><span class="sxs-lookup"><span data-stu-id="f6637-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="f6637-107">Stos wywołań wyjątków zaczyna się od System.Windows.Threading.Dispatcher.VerifyAccess() w System.Windows.DependencyObject.GetValue (DependencyProperty dp) na System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject. element) ten wyjątek może wystąpić w programie .net 4.5, jeśli aplikacja ma więcej niż jeden wątek dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="f6637-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .Net 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="f6637-108">W środowisku .net 4.7 wyjątek może również wystąpić w aplikacji za pomocą pojedynczego Wątek dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="f6637-108">In .Net 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="f6637-109">Problem został rozwiązany w .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f6637-109">The issue is fixed in .Net 4.7.1.</span></span>|
|<span data-ttu-id="f6637-110">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f6637-110">Suggestion</span></span>|<span data-ttu-id="f6637-111">Uaktualnij platformę .net 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f6637-111">Upgrade to .Net 4.7.1.</span></span>|
|<span data-ttu-id="f6637-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="f6637-112">Scope</span></span>|<span data-ttu-id="f6637-113">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="f6637-113">Minor</span></span>|
|<span data-ttu-id="f6637-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="f6637-114">Version</span></span>|<span data-ttu-id="f6637-115">4.7</span><span class="sxs-lookup"><span data-stu-id="f6637-115">4.7</span></span>|
|<span data-ttu-id="f6637-116">Typ</span><span class="sxs-lookup"><span data-stu-id="f6637-116">Type</span></span>|<span data-ttu-id="f6637-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f6637-117">Runtime</span></span>|
