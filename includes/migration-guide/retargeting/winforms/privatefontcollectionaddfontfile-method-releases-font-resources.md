### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>Metoda PrivateFontCollection.AddFontFile zwalnia zasoby czcionki

|   |   |
|---|---|
|Szczegóły|W poprzednich wersjach i .NET Framework 4.7.1 <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> klasy nie zwalnia zasoby czcionek GDI + po <xref:System.Drawing.Text.PrivateFontCollection> usunięciu dla <xref:System.Drawing.Font> obiektów, które są dodawane do tej kolekcji przy użyciu <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> — metoda. W programie .NET Framework 4.7.2 i później <xref:System.Drawing.Text.FontCollection.Dispose%2A> zwalnia czcionek GDI +, które zostały dodane do kolekcji jako plików.|
|Sugestia|<strong>Jak zgłosić do lub z tych zmian do</strong>w kolejności dla aplikacji, aby korzystać z tych zmian, należy uruchomić w programie .NET Framework 4.7.2 lub nowszym. Aplikacji mogą korzystać z tych zmian w jednym z następujących sposobów:<ul><li>Jest ponownie kompilowana docelową programu .NET Framework 4.7.2. Ta zmiana jest domyślnie włączona w aplikacji formularzy systemu Windows, które odnoszą się do programu .NET Framework 4.7.2 lub nowszej.</li><li>Dotyczy programu .NET Framework 4.7.1 lub starszej wersji i wyłącza funkcję zachowania starszych ułatwień dostępu przez dodanie poniższego [przełącznika AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> sekcji w pliku app.config i ustawieniem dla niego <code>false</code>, jak pokazano na poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje, które odnoszą się do programu .NET Framework 4.7.2 lub później i chcesz zachować starszego zachowanie zgodzić się na nie zwolnić zasoby czcionki, jawnie ustawiając tego przełącznika AppContext na <code>true</code>.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|
