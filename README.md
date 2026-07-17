# KI-Agenten Armee (n8n Workflow)

n8n-Workflow-Sammlung für ein Team aus KI-Agenten: Ein Manager-Agent (Telegram) nimmt Anfragen entgegen und delegiert per Sub-Workflow an spezialisierte Agenten für E-Mail, Kalender, Kontakte, Notizen und Social Media.

## Architektur

- **Manager-Agent** – Telegram-Trigger, orchestriert alle Sub-Agenten über `Execute Workflow`-Tools, eigenes Memory (Window Buffer), zusätzlich HTTP-Request- und Calculator-Tool
- **Email-Agent** – Gmail-Tools (lesen, senden, entwerfen, suchen, Labels)
- **Kalender-Agent** – Google-Calendar-Tools (Termine erstellen, suchen, aktualisieren, löschen)
- **Kontakte-Agent** – Google-Sheets-Tools als Kontakt-Datenbank
- **Notizen-Agent** – Notion-Tools (Seiten erstellen/aktualisieren)
- **Social-Media-Agent** – Google-Sheets-Tool für Content-Planung

Jeder Sub-Agent ist ein eigener Workflow mit `Execute Workflow Trigger` und wird vom Manager-Agent als Tool aufgerufen (OpenAI Chat Model + AI Agent je Sub-Workflow).

## Inhalt

- `Manager___Agent (1).json` – Manager-Agent (Telegram-Trigger, Orchestrierung)
- `Email__Agent.json` – E-Mail-Agent (Gmail)
- `Kalender___Agent (1).json` – Kalender-Agent (Google Calendar)
- `Kontake___Agent (1).json` – Kontakte-Agent (Google Sheets)
- `Notizen___Agent (1).json` – Notizen-Agent (Notion)
- `Social_Media___Agent (2).json` – Social-Media-Agent (Google Sheets)
- `KI-Agenten-Team_für_automatisierte_Workflows.png` – Architektur-Übersicht
- `Screenshot 2026-07-17 100417.png` – Screenshot
- `Vom Einzelkämpfer zum digitalen Imperium_ Warum du ein Team aus KI-Agenten brauchst (und wie du es ohne Code baust).pdf` – Begleitartikel

## Übersicht

![Architektur-Übersicht](KI-Agenten-Team_für_automatisierte_Workflows.png)

## Screenshots

![Screenshot 1](Screenshot%202026-07-17%20100417.png)

## Setup

1. Alle sechs JSON-Dateien in n8n importieren
2. Credentials verknüpfen: Telegram, OpenAI API, Gmail, Google Calendar, Google Sheets, Notion
3. Sub-Workflows im Manager-Agent per `Execute Workflow`-Tool referenzieren (Workflow-IDs nach Import anpassen)
4. Manager-Workflow aktivieren

## Verwendete Nodes

- Telegram Trigger / Telegram
- OpenAI Chat Model (`lmChatOpenAi`) + AI Agent (`@n8n/n8n-nodes-langchain.agent`)
- Execute Workflow Trigger / Tool Workflow
- Memory Buffer Window
- HTTP Request Tool, Calculator Tool
- Gmail Tool, Google Calendar Tool, Google Sheets Tool, Notion Tool
