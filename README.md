# 👻 Ghost Säkerhetsmodul
**PowerShell-Baserat Windows & Azure Säkerhetshärdningsverktyg**

> **Proaktiv säkerhetshärdning för Windows-slutpunkter och Azure-miljöer.** Ghost tillhandahåller PowerShell-baserade härdningsfunktioner som kan hjälpa till att minska vanliga angreppsvektorer genom att inaktivera onödiga tjänster och protokoll.

## ⚠️ Viktiga Ansvarsfriskrivningar

**TESTNING KRÄVS**: Testa alltid Ghost i icke-produktionsmiljöer först. Inaktivering av tjänster kan påverka legitima affärsfunktioner.

**INGA GARANTIER**: Även om Ghost riktar sig mot vanliga angreppsvektorer kan inget säkerhetsverktyg förhindra alla attacker. Detta är en komponent i en omfattande säkerhetsstrategi.

**OPERATIV PÅVERKAN**: Vissa funktioner kan påverka systemfunktionalitet. Granska varje inställning noggrant före implementering.

**PROFESSIONELL BEDÖMNING**: För produktionsmiljöer, konsultera säkerhetsproffs för att säkerställa att inställningarna stämmer överens med din organisations behov.

## 📊 Säkerhetslandskapet

Ransomware-skador nådde **57 miljarder dollar under 2025**, med forskning som indikerar att många framgångsrika attacker utnyttjar grundläggande Windows-tjänster och felkonfigurationer. Vanliga angreppsvektorer inkluderar:

- **90% av ransomware-incidenter** involverar RDP-exploatering
- **SMBv1-sårbarheter** möjliggjorde attacker som WannaCry och NotPetya  
- **Dokumentmakron** förblir en primär leveransmetod för malware
- **USB-baserade attacker** fortsätter att rikta sig mot luftgapade nätverk
- **PowerShell-missbruk** har ökat betydligt under de senaste åren

## 🛡️ Ghost Säkerhetsfunktioner

Ghost tillhandahåller **16 Windows-härdningsfunktioner** plus **Azure-säkerhetsintegration**:

### Windows Slutpunktshärdning

| Funktion | Syfte | Överväganden |
|----------|-------|-------------|
| `Set-RDP` | Hanterar Remote Desktop-åtkomst | Kan påverka fjärradministration |
| `Set-SMBv1` | Kontrollerar gammalt SMB-protokoll | Krävs för mycket gamla system |
| `Set-AutoRun` | Kontrollerar AutoPlay/AutoRun | Kan påverka användarbekvämlighet |
| `Set-USBStorage` | Begränsar USB-lagringsenheter | Kan påverka legitim USB-användning |
| `Set-Macros` | Kontrollerar Office-makrokörning | Kan påverka makroaktiverade dokument |
| `Set-PSRemoting` | Hanterar PowerShell-fjärrstyrning | Kan påverka fjärrhantering |
| `Set-WinRM` | Kontrollerar Windows Remote Management | Kan påverka fjärradministration |
| `Set-LLMNR` | Hanterar namnupplösningsprotokoll | Vanligtvis säkert att inaktivera |
| `Set-NetBIOS` | Kontrollerar NetBIOS över TCP/IP | Kan påverka äldre applikationer |
| `Set-AdminShares` | Hanterar administrativa delningar | Kan påverka fjärrfilåtkomst |
| `Set-Telemetry` | Kontrollerar datainsamling | Kan påverka diagnostikkapacitet |
| `Set-GuestAccount` | Hanterar Gästkonto | Vanligtvis säkert att inaktivera |
| `Set-ICMP` | Kontrollerar ping-svar | Kan påverka nätverksdiagnostik |
| `Set-RemoteAssistance` | Hanterar Fjärrhjälp | Kan påverka helpdesk-verksamhet |
| `Set-NetworkDiscovery` | Kontrollerar nätverksupptäckt | Kan påverka nätverksbläddring |
| `Set-Firewall` | Hanterar Windows Brandvägg | Kritisk för nätverkssäkerhet |

### Azure Molnsäkerhet

| Funktion | Syfte | Krav |
|----------|-------|------|
| `Set-AzureSecurityDefaults` | Aktiverar grundläggande Azure AD-säkerhet | Microsoft Graph-behörigheter |
| `Set-AzureConditionalAccess` | Konfigurerar åtkomstpolicyer | Azure AD P1/P2-licensiering |
| `Set-AzurePrivilegedUsers` | Granskar privilegierade konton | Global Admin-behörigheter |

### Företagsimplementeringsalternativ

| Metod | Användningsfall | Krav |
|-------|----------------|------|
| **Direkt Exekvering** | Testning, små miljöer | Lokala administratörsrättigheter |
| **Group Policy** | Domänmiljöer | Domänadmin, GP-hantering |
| **Microsoft Intune** | Molnhanterade enheter | Intune-licensiering, Graph API |

## 🚀 Snabbstart

### Säkerhetsbedömning
```powershell
# Ladda Ghost-modul
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Kontrollera aktuell säkerhetsposition
Get-Ghost
```

### Grundläggande Härdning (Testa Först)
```powershell
# Väsentlig härdning - testa i labbmiljö först
Set-Ghost -SMBv1 -AutoRun -Macros

# Granska ändringar
Get-Ghost
```

### Företagsimplementering
```powershell
# Group Policy-implementering (domänmiljöer)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune-implementering (molnhanterade enheter)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Installationsmetoder

### Alternativ 1: Direkt Nedladdning (Testning)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Alternativ 2: Modulinstallation
```powershell
# Installera från PowerShell Gallery (när tillgängligt)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Alternativ 3: Företagsimplementering
```powershell
# Kopiera till nätverksplats för Group Policy-implementering
# Konfigurera Intune PowerShell-skript för molnimplementering
```

## 💼 Användningsfallsexempel

### Småföretag
```powershell
# Grundläggande skydd med minimal påverkan
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Sjukvårdsmiljö
```powershell
# HIPAA-fokuserad härdning
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finansiella Tjänster
```powershell
# Högsäkerhetskonfiguration
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Moln-Först Organisation
```powershell
# Intune-hanterad implementering
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Funktionsdetaljer

### Kärnhärdningsfunktioner

#### Nätverkstjänster
- **RDP**: Blockerar fjärrskrivbordsåtkomst eller slumpar port
- **SMBv1**: Inaktiverar gammalt fildelningsprotokoll
- **ICMP**: Förhindrar ping-svar för rekognosering
- **LLMNR/NetBIOS**: Blockerar gamla namnupplösningsprotokoll

#### Applikationssäkerhet  
- **Makron**: Inaktiverar makrokörning i Office-applikationer
- **AutoRun**: Förhindrar automatisk exekvering från flyttbara media

#### Fjärrhantering
- **PSRemoting**: Inaktiverar PowerShell-fjärrsessioner
- **WinRM**: Stoppar Windows Remote Management
- **Remote Assistance**: Blockerar fjärrhjälpsanslutningar

#### Åtkomstkontroll
- **Admin Shares**: Inaktiverar C$, ADMIN$-delningar
- **Guest Account**: Inaktiverar Gästkontoåtkomst
- **USB Storage**: Begränsar USB-enhetsanvändning

### Azure-integration
```powershell
# Anslut till Azure-hyresgäst
Connect-AzureGhost -Interactive

# Aktivera säkerhetsstandarder
Set-AzureSecurityDefaults -Enable

# Konfigurera villkorlig åtkomst
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Granska privilegierade användare
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune-integration (Nytt i v2)
```powershell
# Anslut till Intune
Connect-IntuneGhost -Interactive

# Implementera via Intune-policyer
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Viktiga Överväganden

### Testningskrav
- **Labbmiljö**: Testa alla inställningar i isolerad miljö först
- **Fasad Implementering**: Rulla ut gradvis för att identifiera problem
- **Återställningsplan**: Se till att du kan återställa ändringar om det behövs
- **Dokumentation**: Dokumentera vilka inställningar som fungerar för din miljö

### Potentiell Påverkan
- **Användarproduktivitet**: Vissa inställningar kan påverka dagliga arbetsflöden
- **Äldre Applikationer**: Äldre system kan kräva vissa protokoll
- **Fjärråtkomst**: Överväg påverkan på legitim fjärradministration
- **Affärsprocesser**: Verifiera att inställningar inte bryter kritiska funktioner

### Säkerhetsbegränsningar
- **Fördjupad Försvar**: Ghost är ett lager av säkerhet, inte en komplett lösning
- **Pågående Hantering**: Säkerhet kräver kontinuerlig övervakning och uppdateringar
- **Användarutbildning**: Tekniska kontroller måste paras med säkerhetsmedvetenhet
- **Hot Evolution**: Nya attackmetoder kan kringgå nuvarande skydd

## 🎯 Exempel på Attackscenarier

Medan Ghost riktar sig mot vanliga angreppsvektorer beror specifik förebyggande på korrekt implementering och testning:

### WannaCry-Stil Attacker
- **Begränsning**: `Set-Ghost -SMBv1` inaktiverar det sårbara protokollet
- **Övervägande**: Se till att inga äldre system kräver SMBv1

### RDP-Baserad Ransomware
- **Begränsning**: `Set-Ghost -RDP` blockerar fjärrskrivbordsåtkomst
- **Övervägande**: Kan kräva alternativa fjärråtkomstmetoder

### Dokumentbaserad Malware
- **Begränsning**: `Set-Ghost -Macros` inaktiverar makrokörning
- **Övervägande**: Kan påverka legitima makroaktiverade dokument

### USB-Levererade Hot
- **Begränsning**: `Set-Ghost -USBStorage -AutoRun` begränsar USB-funktionalitet
- **Övervägande**: Kan påverka legitim USB-enhetsanvändning

## 🏢 Företagsfunktioner

### Group Policy-stöd
```powershell
# Tillämpa inställningar via Group Policy-registret
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Inställningar tillämpas domänövergripande efter GP-uppdatering
gpupdate /force
```

### Microsoft Intune-integration
```powershell
# Skapa Intune-policyer för Ghost-inställningar
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Policyer implementeras automatiskt på hanterade enheter
```

### Efterlevnadsrapportering
```powershell
# Generera säkerhetsbedömningsrapport
Get-Ghost | Export-Csv -Path "SäkerhetsRevision-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure-säkerhetspositionsrapport
Get-AzureGhost | Out-File "AzureSäkerhetsRapport.txt"
```

## 📚 Bästa Praxis

### Pre-Implementering
1. **Dokumentera Nuvarande Tillstånd**: Kör `Get-Ghost` före ändringar
2. **Testa Noggrant**: Validera i icke-produktionsmiljö
3. **Planera Återställning**: Veta hur man återställer varje inställning
4. **Intressentgranskning**: Se till att affärsenheter godkänner ändringar

### Under Implementering
1. **Fasad Approach**: Implementera till pilotgrupper först
2. **Övervaka Påverkan**: Håll utkik efter användarklagomål eller systemproblem
3. **Dokumentera Problem**: Registrera eventuella problem för framtida referens
4. **Kommunicera Ändringar**: Informera användare om säkerhetsförbättringar

### Efter Implementering
1. **Regelbunden Bedömning**: Kör periodiskt `Get-Ghost` för att verifiera inställningar
2. **Uppdatera Dokumentation**: Håll säkerhetskonfigurationer aktuella
3. **Granska Effektivitet**: Övervaka för säkerhetsincidenter
4. **Kontinuerlig Förbättring**: Justera inställningar baserat på hotlandskap

## 🔧 Felsökning

### Vanliga Problem
- **Behörighetsfel**: Se till att du har förhöjd PowerShell-session
- **Tjänstberoenden**: Vissa tjänster kan ha beroenden
- **Applikationskompatibilitet**: Testa med affärsapplikationer
- **Nätverksanslutning**: Verifiera att fjärråtkomst fortfarande fungerar

### Återställningsalternativ
```powershell
# Återaktivera specifika tjänster om det behövs
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Om Författaren

**Jim Tyler** - Microsoft MVP för PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10 000+ prenumeranter)
- **Nyhetsbrev**: [PowerShell.News](https://powershell.news) - Veckovis säkerhetsinformation
- **Författare**: "PowerShell for Systems Engineers"
- **Erfarenhet**: Decennier av PowerShell-automatisering och Windows-säkerhet

## 📄 Licens & Ansvarsfriskrivning

### MIT-licens
Ghost tillhandahålls under MIT-licensen för fri användning, modifiering och distribution.

### Säkerhetsansvarsfriskrivning
- **Ingen Garanti**: Ghost tillhandahålls "som det är" utan garanti av något slag
- **Testning Krävs**: Testa alltid i icke-produktionsmiljöer först
- **Professionell Vägledning**: Konsultera säkerhetsproffs för produktionsimplementeringar
- **Operativ Påverkan**: Författarna är inte ansvariga för eventuella operativa störningar
- **Omfattande Säkerhet**: Ghost är en komponent i en komplett säkerhetsstrategi

### Support
- **GitHub Issues**: [Rapportera buggar eller begär funktioner](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentation**: Använd `Get-Help <funktion> -Full` för detaljerad hjälp
- **Gemenskap**: PowerShell och säkerhetsgemenskapsforum

---

**🔒 Stärk din säkerhetsposition med Ghost - men testa alltid först.**

```powershell
# Börja med bedömning, inte antaganden
Get-Ghost
```

**⭐ Stjärnmärk detta repository om Ghost hjälper till att förbättra din säkerhetsposition!**