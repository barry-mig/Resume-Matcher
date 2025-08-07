# Resume Matcher - Complete Dependencies and Tools Guide

This document provides a comprehensive overview of all tools, dependencies, and requirements needed to successfully run the Resume Matcher project.

## 📋 System Requirements

### Operating System Support
- **Windows**: 10/11 with PowerShell 5.1+
- **macOS**: 10.15+ (Catalina or later)
- **Linux**: Ubuntu 18.04+, Debian 10+, or equivalent distributions

### Minimum Hardware Requirements
- **RAM**: 8GB minimum, 16GB recommended (for AI model operations)
- **Storage**: 10GB free space (for dependencies and AI models)
- **CPU**: x64 architecture with SSE4.2 support

## 🛠️ Core System Tools

### Required System Tools

| Tool | Minimum Version | Purpose | Installation |
|------|----------------|---------|--------------|
| **Node.js** | v18.0.0+ | JavaScript runtime for frontend | [nodejs.org](https://nodejs.org/) |
| **npm** | v8.0.0+ | Package manager (included with Node.js) | Comes with Node.js |
| **Python** | v3.12.0+ | Backend runtime | [python.org](https://python.org/downloads/) |
| **pip** | v21.0+ | Python package installer | Included with Python |
| **Git** | v2.25+ | Version control | [git-scm.com](https://git-scm.com/) |
| **UV** | Latest | Modern Python package manager | Auto-installed by setup scripts |
| **Ollama** | v0.6.7+ | Local AI model server | [ollama.com](https://ollama.com/) |

### Platform-Specific Tools

#### Windows Additional Requirements
- **PowerShell** 5.1+ or PowerShell Core 7+
- **Windows Package Manager (winget)** - for automated installations
- **Visual C++ Redistributable** - for some Python packages

#### Linux/macOS Additional Requirements
- **Bash** 4.4+ (for setup scripts)
- **curl** - for downloading tools
- **make** - for Makefile commands (optional but recommended)

## 🐍 Backend Dependencies (Python)

### Core Framework
```
fastapi==0.115.12          # Modern web framework
uvicorn==0.34.0            # ASGI server
starlette==0.46.1          # Web framework foundation
```

### Database & ORM
```
SQLAlchemy==2.0.40         # Database ORM
aiosqlite==0.21.0          # Async SQLite driver
```

### AI & Machine Learning
```
ollama==0.4.7              # Local AI model integration
openai==1.75.0             # OpenAI API client
onnxruntime==1.21.1        # ONNX model runtime
numpy==2.2.4               # Numerical computations
```

### Document Processing
```
pdfminer.six==20250327     # PDF text extraction
beautifulsoup4==4.13.4     # HTML parsing
html2text==2025.4.15       # HTML to text conversion
markitdown==0.1.1          # Markdown processing
magika==0.6.1              # File type detection
```

### HTTP & Networking
```
httpx==0.28.1              # Async HTTP client
requests==2.32.3           # HTTP library
```

### Validation & Configuration
```
pydantic==2.11.3           # Data validation
pydantic-settings==2.8.1   # Settings management
python-dotenv==1.1.0       # Environment variables
email_validator==2.2.0     # Email validation
```

### Security & Cryptography
```
cryptography==44.0.2       # Cryptographic utilities
```

### Development & Utilities
```
python-multipart==0.0.20   # File upload support
coloredlogs==15.0.1        # Colored logging
tqdm==4.67.1               # Progress bars
```

## ⚛️ Frontend Dependencies (JavaScript/TypeScript)

### Core Framework
```
next@15.3.0                # React framework
react@^19.0.0              # UI library
react-dom@^19.0.0          # React DOM renderer
typescript@^5              # Type safety
```

### UI Components & Styling
```
@radix-ui/react-dialog@^1.1.13     # Modal components
@radix-ui/react-label@^2.1.4       # Label components
@radix-ui/react-slot@^1.2.0        # Slot components
lucide-react@^0.501.0              # Icon library
```

### Styling System
```
tailwindcss@^4             # Utility-first CSS framework
@tailwindcss/postcss@^4    # PostCSS integration
clsx@^2.1.1                # Conditional classes
tailwind-merge@^3.2.0      # Tailwind class merging
class-variance-authority@^0.7.1  # Component variants
```

### Animation
```
motion@^12.7.4             # Animation library
tw-animate-css@^1.2.5      # Tailwind animations
```

### Development Tools
```
eslint@^9.27.0             # Code linting
eslint-config-next@15.3.0  # Next.js ESLint config
eslint-config-prettier@^10.1.5  # Prettier integration
eslint-plugin-prettier@^5.4.0   # Prettier plugin
prettier@^3.5.3            # Code formatting
```

## 🤖 AI Model Requirements

### Ollama Models
The project requires the following AI model to be downloaded:

```bash
ollama pull gemma3:4b
```

**Model Details:**
- **Name**: gemma3:4b
- **Size**: ~2.6GB
- **Purpose**: Resume analysis and matching
- **Requirements**: 4GB+ RAM available for model operations

### Model Storage
- **Location**: Ollama manages model storage automatically
- **Disk Space**: ~3GB per model
- **Performance**: Better with dedicated GPU (optional)

## 📁 Project Structure Dependencies

### Configuration Files
```
├── package.json              # Root npm dependencies
├── apps/
│   ├── backend/
│   │   ├── pyproject.toml     # Python project config
│   │   ├── requirements.txt   # Python dependencies
│   │   └── .env.sample        # Backend environment template
│   └── frontend/
│       ├── package.json       # Frontend dependencies
│       ├── next.config.ts     # Next.js configuration
│       ├── tailwind.config.js # Tailwind configuration
│       ├── tsconfig.json      # TypeScript configuration
│       └── .env.sample        # Frontend environment template
├── setup.sh                  # Linux/macOS setup script
├── setup.ps1                 # Windows setup script
└── Makefile                  # Make commands (Linux/macOS)
```

### Environment Variables

#### Backend (.env)
```
SESSION_SECRET_KEY="a-secret-key"
SYNC_DATABASE_URL="sqlite:///./app.db"
ASYNC_DATABASE_URL="sqlite+aiosqlite:///./app.db"
PYTHONDONTWRITEBYTECODE=1
```

#### Frontend (.env)
```
NEXT_PUBLIC_API_URL=http://localhost:8000
```

## 🚀 Development Dependencies

### Build Tools
```
concurrently@^9.1.2         # Run multiple commands
```

### Additional Dev Tools (Auto-installed)
- **UV**: Modern Python dependency management
- **PostCSS**: CSS processing
- **ESLint**: JavaScript/TypeScript linting
- **Prettier**: Code formatting

## 📦 Package Managers Used

1. **npm** - Root project and frontend JavaScript dependencies
2. **UV** - Backend Python dependencies (modern pip alternative)
3. **Ollama** - AI model management

## 🔧 Setup Process Overview

### Automated Setup
The project includes automated setup scripts that handle:

1. **Dependency Installation**
   - Verifies and installs system requirements
   - Installs UV (Python package manager)
   - Installs Ollama (if not present)

2. **Environment Configuration**
   - Creates .env files from templates
   - Configures database connections
   - Sets up API endpoints

3. **Package Installation**
   - Installs root npm dependencies
   - Installs frontend dependencies
   - Installs backend Python dependencies via UV

4. **AI Model Setup**
   - Downloads and configures gemma3:4b model
   - Verifies Ollama service

### Manual Verification Commands
```bash
# Check Node.js and npm
node --version && npm --version

# Check Python and pip
python3 --version && pip3 --version

# Check UV installation
uv --version

# Check Ollama installation
ollama --version

# Verify AI model
ollama list | grep gemma3
```

## ⚡ Performance Considerations

### Memory Usage
- **Frontend Development**: ~500MB RAM
- **Backend API**: ~1GB RAM
- **Ollama + AI Model**: ~4GB RAM
- **Total Recommended**: 8GB+ RAM

### Network Requirements
- Initial setup requires internet for downloading:
  - Node.js dependencies (~200MB)
  - Python dependencies (~500MB)
  - AI model (~2.6GB)

## 🐛 Common Issues & Solutions

### Windows-specific Issues
- **PowerShell Execution Policy**: Run `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
- **Python PATH Issues**: Ensure Python is added to system PATH
- **UV Installation**: May require terminal restart after installation

### Linux/macOS Issues
- **Permission Errors**: Use `chmod +x setup.sh` before running
- **Python Version**: Ensure python3 points to Python 3.12+
- **Ollama Service**: Ensure Ollama service is running with `ollama serve`

### General Issues
- **Port Conflicts**: Ensure ports 3000 (frontend) and 8000 (backend) are available
- **Disk Space**: Ensure 10GB+ free space before setup
- **Network Firewall**: Allow Ollama to download models

## 📋 Quick Start Checklist

- [ ] Install Node.js 18+ and npm
- [ ] Install Python 3.12+ and pip
- [ ] Install Git
- [ ] Clone the repository
- [ ] Run setup script (`./setup.sh` or `.\setup.ps1`)
- [ ] Verify Ollama is running (`ollama serve`)
- [ ] Start development server (`npm run dev`)
- [ ] Access application at http://localhost:3000

## 🔗 Additional Resources

- [Official Setup Guide](SETUP.md)
- [Node.js Installation](https://nodejs.org/)
- [Python Installation](https://python.org/downloads/)
- [Ollama Documentation](https://ollama.com/docs)
- [UV Documentation](https://docs.astral.sh/uv/)

---

*Last updated: January 2025*