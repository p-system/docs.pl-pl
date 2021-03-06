---
title: 'Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231516"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)
Ten przewodnik zawiera podstawowe scenariusz start zakończenie wyświetlanie powiązanych danych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="prerequisite"></a>Wymaganie wstępne  
 W tym przewodniku wymaga przykładowej bazy danych Northwind.  
  
 Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Omówienie  
 Pierwsza część tego przewodnika składa się z czterech głównych zadań:  
  
-   Tworzenie rozwiązania.  
  
-   Dodawanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
-   Dodawanie źródła danych.  
  
-   Dodawanie formantów powiązanych z danymi.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Tworzenie rozwiązania DataRepeater  
 W pierwszym kroku możesz utworzyć projektu i rozwiązania.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Tworzenie rozwiązań DataRepeater  
  
1.  W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2.  W **typy projektów** okienka w **nowy projekt** okna dialogowego rozwiń **Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji Windows Forms**.  
  
4.  W **nazwa** wpisz `DataRepeaterApp`.  
  
5.  Kliknij przycisk **OK**.  
  
     Zostanie otwarty projektant formularzy systemu Windows.  
  
6.  Wybierz formularza w narzędziu Projektant dla formularzy systemu Windows. W **właściwości** ustaw **rozmiar** właściwości `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Dodawanie formantu DataRepeater  
 W tym kroku, możesz dodać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania do formularza.  
  
#### <a name="to-add-a-datarepeater-control"></a>Aby dodać formantu DataRepeater  
  
1.  Na **widoku** menu, kliknij przycisk **przybornika**.  
  
     **Przybornika** otwiera.  
  
2.  Wybierz **Visual Basic PowerPacks** kartę.  
  
3.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować na **Form1**.  
  
4.  W oknie właściwości ustaw **lokalizacji** właściwości `0, 25`.  
  
5.  Ustaw **rozmiar** właściwości `460, 600`.  
  
## <a name="adding-a-data-source"></a>Dodawanie źródła danych  
 W tym kroku, Dodaj źródło danych dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
#### <a name="to-add-a-data-source"></a>Aby dodać źródła danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
2.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładowej bazy danych Northwind jest dostępny na liście rozwijanej, kliknij go.  
  
         —lub—  
  
    -   Kliknij przycisk **nowe połączenie** można skonfigurować nowe połączenia danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](/visualstudio/data-tools/add-new-connections).  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie kliknij przycisk **dalej**.  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlone okno dialogowe, kliknij przycisk **tak** można zapisać pliku do projektu.  
  
6.  Kliknij przycisk **dalej** na **zapisać parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
7.  Rozwiń węzeł **tabel** węzła na **wybierz obiekty bazy danych użytkownika** strony.  
  
8.  Zaznacz pole wyboru obok pozycji **klientów** i **zamówień** tabel, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i **klientów** i **zamówień** tabele są wyświetlane w **źródeł danych** okna.  
  
## <a name="adding-data-bound-controls"></a>Dodawanie formantów powiązanych z danymi  
 W tym kroku, Dodaj formanty powiązane z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Aby dodać formanty powiązane z danymi  
  
1.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu **klientów** tabeli.  
  
2.  Zmień typ docelowej tabeli **szczegóły** klikając **szczegóły** na liście rozwijanej na węźle tabeli.  
  
3.  Wybierz **klientów** tabeli węzła i przeciągnij element szablonu regionie (górnej) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     A <xref:System.Windows.Forms.BindingNavigator> formant został dodany do formularza i **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, i **CustomersBindingNavigator** składniki są dodawane do składnika na pasku zadań.  
  
4.  Zaznacz wszystkie pola i ich etykiet skojarzonych i umieść je z lewą krawędzią obszaru szablonu elementu.  
  
5.  Wybierz pola pięć ostatnich (**Region**, **kod pocztowy**, **kraju**, **Phone**, i **faksów**) i ich etykiet skojarzonych i przenieść je w górę i w prawo pierwszych sześciu pól.  
  
6.  Wybierz szablon elementu (górnej formantu).  
  
7.  W oknie właściwości ustaw **rozmiar** właściwości `427, 170`.  
  
 W tym momencie masz działającą aplikację, która będzie wyświetlana identycznych listę klientów. Naciśnij klawisz F5, aby uruchomić aplikację, dane, zmiany i dodawania i usuwania rekordów klientów.  
  
 W następnych kroków opcjonalnych, przedstawiono sposób dostosowywania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="next-steps-optional"></a>Następne kroki (opcjonalnie)  
 Ta część przewodnika obejmuje cztery opcjonalnych zadań:  
  
-   Zmiana wyglądu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
-   Uniemożliwia użytkownikom dodawanie i usuwanie rekordów.  
  
-   Dodawanie możliwości wyszukiwania do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
-   Dodawanie głównego i szczegółów tabeli do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Zmienianie wyglądu formantu DataRepeater  
 W tym kroku opcjonalne, zmień `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania. Możesz również dodać kod, aby wyświetlić wiersze w naprzemiennych kolorów i aby zmienić etykietę `ForeColor` warunkowo.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Aby zmienić wygląd formantu  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz główny region (niższe) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
2.  W oknie właściwości ustaw `BackColor` właściwości na kolor biały.  
  
3.  Kliknij dwukrotnie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> można otworzyć edytora kodu.  
  
4.  W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **DrawItem**.  
  
5.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj następujący kod do alternatywnego `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj następujący kod, aby zmienić `ForeColor` etykiety w zależności od warunek:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Naciśnij klawisz F5, aby uruchomić aplikację i sprawdzić dostosowania.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Uniemożliwia użytkownikom dodawanie i usuwanie rekordów  
 W tym kroku opcjonalnie Dodaj kod, który uniemożliwia użytkownikom dodawanie i usuwanie rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Aby uniemożliwić użytkownikom dodawanie i usuwanie rekordów  
  
1.  W narzędziu Projektant dla formularzy systemu Windows kliknij dwukrotnie formularza, aby otworzyć edytora kodu.  
  
2.  Dodaj następujący kod do `Form_Load` zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Na liście rozwijanej nazwy klasy kliknij **BindingNavigatorDeleteItem**. Na liście rozwijanej nazwy metody kliknij **EnabledChanged**.  
  
4.  Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację. Zwróć uwagę, że **DeleteItem** przycisk jest wyłączony i że nie można usunąć elementów, naciskając klawisz DELETE.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Dodawanie możliwości wyszukiwania do formantu DataRepeater  
 W tym kroku opcjonalne wdrożenia możliwość wyszukiwania wartości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Jeśli zostanie znaleziony ciąg wyszukiwania, formantu wybiera element zawiera wartość, którą można przewinąć element w widoku.  
  
#### <a name="to-add-search-capability"></a>Aby dodać możliwości wyszukiwania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     Umieść go w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
2.  W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Umieść go w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
4.  W oknie Właściwości zmień **nazwa** właściwości **SearchButton**. Zmień **tekst** właściwości **wyszukiwania**.  
  
5.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć edytora kodu i Dodaj następujący kod do `SearchButton_Click` obsługi zdarzeń.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację. Wpisz identyfikator klienta w **SearchTextBox** i kliknij przycisk **wyszukiwania** przycisku.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Dodawanie głównego i Tabela szczegółów do DataRepeater  
 W tym kroku opcjonalne, możesz dodać drugi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu, aby wyświetlić powiązane zamówienia dla każdego klienta.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Aby dodać tabelę wzorca i szczegóły  
  
1.  Przeciągnij drugi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** na formularzu.  
  
2.  W oknie właściwości ustaw **lokalizacji** właściwości `465, 25`.  
  
3.  Ustaw **rozmiar** właściwości `315, 600`.  
  
4.  W **źródeł danych** okna, rozwiń węzeł **klientów** tabeli węzeł, a następnie wybierz węzeł szczegółów **zamówień** tabeli.  
  
5.  Zmień typ listy **zamówień** tabeli, aby uzyskać szczegółowe informacje, klikając **szczegóły** na liście rozwijanej na węźle tabeli.  
  
6.  Przeciągnij **zamówień** węzła tabeli na region szablonu elementu (górnej) drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     **OrdersBindingSource** składnika i **OrdersTableAdapter** składnika są dodawane do składnika na pasku zadań.  
  
7.  Naciśnij klawisz F5, aby uruchomić aplikację. Po wybraniu każdego klienta w pierwszym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować zamówienia dla tego klienta są wyświetlane w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: zmienianie układu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie nagłówków elementów w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyszukiwanie danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
