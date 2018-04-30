### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="70839-101">RSACng i DSACng są ponownie można używać w przypadku zaufania częściowego scenariuszy</span><span class="sxs-lookup"><span data-stu-id="70839-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

|   |   |
|---|---|
|<span data-ttu-id="70839-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="70839-102">Details</span></span>|<span data-ttu-id="70839-103">CngLightup (używane w kilku kryptograficznego wyższego poziomu interfejsów API, takich jak <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) i <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> w niektórych przypadkach zależą od pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="70839-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="70839-104">Obejmują one P/Invokes nie zostanie <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> uprawnienia i ścieżki kodu gdzie <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> ma uprawnienie zapotrzebowanie na <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70839-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="70839-105">Począwszy od programu .NET Framework 4.6.2, aby przełączyć się do użyto CngLightup <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> tam gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="70839-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="70839-106">W związku z tym aplikacje częściowo zaufane który pomyślnie użyta <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> rozpoczęła się niepowodzeniem i zgłosić <xref:System.Security.SecurityException> wyjątków. Ta zmiana dodaje wymaganych potwierdza, tak aby wszystkie funkcje za pomocą CngLightup wymaganych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="70839-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>|
|<span data-ttu-id="70839-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="70839-107">Suggestion</span></span>|<span data-ttu-id="70839-108">Jeśli ta zmiana w programie .NET Framework 4.6.2 ma negatywnego wpływu na aplikacje częściowej relacji zaufania, uaktualnienie do programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="70839-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>|
|<span data-ttu-id="70839-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="70839-109">Scope</span></span>|<span data-ttu-id="70839-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="70839-110">Edge</span></span>|
|<span data-ttu-id="70839-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="70839-111">Version</span></span>|<span data-ttu-id="70839-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="70839-112">4.6.2</span></span>|
|<span data-ttu-id="70839-113">Typ</span><span class="sxs-lookup"><span data-stu-id="70839-113">Type</span></span>|<span data-ttu-id="70839-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="70839-114">Runtime</span></span>|
|<span data-ttu-id="70839-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="70839-115">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
