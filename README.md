# Broke-Jarvis
my hardware is too shitty for hermes agent so i made my own it might work might not for context my hardware is a intel i7 7650u and 8gb ddr3 2133 no dedicated gpoou
BROKE JARVIS

Local-first AI assistant desktop application. Runs on your machine with Ollama. Provides tools: web search, file operations, system monitoring, TTS/STT, and vision. Protected by sandbox and permission system.

FEATURES

- Local AI models - any model installed in Ollama
- Real streaming - token by token
- Tool-using agent - web search, URL fetch, file read/write, app launch, volume control, system status
- Memory - persistent per-session history with bounded context
- File sandboxing - openat2 based secure file access
- SSRF protection - blocks private, loopback, link-local, multicast, reserved IPs
- Image validation - size, pixel, dimension, format checks
- Premium GUI - multiple themes, system monitor, command palette, activity timeline
- Security dispatcher - permission prompts for sensitive actions
- TTS/STT - optional Piper and faster-whisper

REQUIREMENTS

- Linux for openat2 support (other platforms may lack secure sandbox)
- Python 3.10+
- Ollama running locally
- Optional Piper for TTS

INSTALLATION

1. Clone repository
   git clone https://github.com/light-broke/broke-jarvis.git
   cd broke-jarvis

2. Install dependencies
   pip install -r requirements.txt

3. Ensure Ollama is running
   ollama serve

4. Pull a model (example Qwen 2.5)
   ollama pull qwen2.5:3b

5. Run Broke Jarvis
   python main_desktop.py

OPERATING INSTRUCTIONS

Main Interface

- Left navigation: New Chat, Sessions, Files, Settings
- Central workspace: conversation area
- Right panel: model name, CPU/RAM graphs, activity timeline
- Bottom input bar: type messages here

Basic Usage

- Ask a question or give a command: type in input and press Enter or click SEND
- Attach an image: click the paperclip button, select PNG/JPEG/WEBP
- Stop generation: click the stop button (square icon)
- Open command palette: press Ctrl+K
- Change theme: go to Settings (left navigation), select theme dropdown

Available Commands and Tools

Broke Jarvis can perform actions when the model requests them. These actions require your approval for sensitive operations.

Examples of what you can ask:
- "Search the web for latest AI news"
- "Open firefox"
- "Write a file named notes.txt with content hello"
- "Read the file report.txt from Documents"
- "Open the website example.com"
- "Mute volume"
- "Show system status"

Permission Prompts

When the agent wants to perform a sensitive action (write file, launch unknown app, use external network), a dialog appears asking Allow or Deny. Always review the details before allowing. Deny is the default.

Themes

Broke Jarvis includes five themes:
- Midnight (default) - premium dark dashboard
- F-Society - terminal/glitch style
- Cyberpunk - neon purple/cyan
- Blade Runner - noir amber
- Minimal - clean light professional

Switch themes live in Settings.

SECURITY NOTES

- No shell execution - all external programs run with argument lists only
- File operations restricted to Documents, Downloads, Projects, and Workspace folders
- openat2 prevents symlink escape and path traversal
- URL safety checks block private and local IP addresses
- Permission dialogs required for write, external network, unknown app launch
- All sensitive files stored with 0700 directories and 0600 files

RUNNING TESTS

Run the test suite:
   pytest test_suite.py -v


Linux specific
Create a virtual environment named venv (or any name you prefer):
python3 -m venv venv
source venv/bin/activate

   Install all dependencies from requirements.txt:
pip install -r requirements.txt

To run Broke Jarvis:
python main_desktop.py
