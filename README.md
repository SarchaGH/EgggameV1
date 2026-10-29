# EgggameV1

## **Egg Game - 2D Platformer**

Dette er et 2D-plattformspill utviklet i Unity 6 som en del av prosjektoppgaven. 

Spilleren kontrollerer en egg-figur ("EGG") som må navigere gjennom hindringer, samle mynter og gjennomføre nivåene uten å ta for mye fallskade.



\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



1. #### **SPILLETS MÅL OG MÅLGRUPPEÆ**



- **Spillets mål:** Navigere trygt gjennom nivåene, samle flest mulig mynter, og komme seg helskinnet til slutten av brettet uten å miste all helse.


- **Målgruppe:** Spillere i alle aldre som liker klassiske og utfordrende 2D-plattformspill.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_


2. ####  **KONTROLLERE**



- **A / D eller Venstre / Høyre piltast:** Bevege spilleren til venstre og høyre.


- **F:** Veksle mellom fullskjerm (Fullscreen) og vindus modus (Windowed).


- **Spacebar:** Hoppe.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_


3. ####  **FUNKSJONER OG MEKANIKKER**



- **Bevegelse og Fysikk:** Spilleren har fysikk basert bevegelse med Rigidbody2D for hopping og løping.

<img src="./readmeimg/gameplay1.png" width="400" alt="Move-img">

- **Helsesystem og Fallskade:** Spilleren har helsemålet. Hvis spilleren faller fra stor høyde med høy hastighet (safeFallSpeed), tas det skade basert på fallhastigheten.

<img src="./readmeimg/gameplay2.png" width="400" alt="falldmg-img">

- **Persistent Myntsystem:** Mynter og samleobjekter blir registrert i en sentral Game Manager. Når en mynt er samlet opp, 
blir ID-en lagret slik at den ikke dukker opp igjen ved omstart, og den totale verdien bevares på tvers av nivåer (DontDestroyOnLoad).


- **Automatisk Omstart (Auto-Restart):** Når helsen når 0, tilbakestilles brettet automatisk og umiddelbart via Scene Manager, uten at samlede mynter mistes.


- **Skjerm styring:** Egen funksjon i Game Manager for å bytte til fullskjerm ved å trykke på F.



\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

4. ####  **KILDEKODE OG EKSEMPLE**



**Eksempel : GameManager.cs (Singleton \& Data Persistence)C#**


```C#
using UnityEngine;
using System.Collections.Generic;

public class GameManager : MonoBehaviour
 {
  public static GameManager Instance;
  public int totalCoins = 0;
  public List<string> collectedCoins = new List<string>();


private void Awake()
 {
     if (Instance == null)
     {
       Instance = this;
       DontDestroyOnLoad(gameObject);
     }
     else
     {
         Destroy(gameObject);
     }
 }


void Update()

 {
     if (Input.GetKeyDown(KeyCode.F))
     {
         Screen.fullScreen = !Screen.fullScreen;
     }
 }
 }

```

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



5. ####  **TEKNISKE DETALJER OG VERKTØY**



- **Spillmotor:** Unity 6


- **Programmeringsspråk**: C#


- **Utviklingsverktøy:** Visual Studio / Visual Studio Code

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



6. #### **BRUK AV KI**


**Microsoft Copilot**

- **Bruk:** Forstå og tolke oppgaveteksten og vurderingskriteriene.

- **Nytte:** Hjalp meg med å lage en tydelig sjekkliste for innleveringen.

**Gemini**
- **Bruk:** Hjelp til noen av C#-skripting, feilsøking og råd om Unity-funksjoner.

- **Eksempler på prompter:**

- "Hvordan gjør jeg slik at brettet resettes automatisk ved død uten at myntene forsvinner?"

- "Hvordan bruker jeg GameManager med DontDestroyOnLoad for å ta med mynter fra Level 1 til Level 2?"

<img src="./readmeimg/AI!.png" width="400" alt="AIuse-img">

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



7. ####  **HVORDAN KJØRE SPILLET**

 - Åpne prosjektmappen i Unity Hub (versjon Unity 6 eller nyere).

 - Naviger til mappen Assets/Scenes/.

 - Åpne scenen LV1 (Level 1).

 - Trykk på Play-knappen øverst i Unity-editoren for å starte spillet.


\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

