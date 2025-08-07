# Resume Matcher - Quick Setup Summary

## 🎯 What You Need to Run Resume Matcher Successfully

### Essential Tools (Install First)
1. **Node.js 18+** with npm → https://nodejs.org/
2. **Python 3.12+** with pip → https://python.org/downloads/
3. **Git** → https://git-scm.com/

### Auto-Installed by Setup Scripts
- **UV** (Python package manager)
- **Ollama** (AI model server)
- **gemma3:4b** AI model (~2.6GB download)

## 🚀 One-Command Setup

### Windows (PowerShell)
```powershell
git clone https://github.com/srbhr/Resume-Matcher.git
cd Resume-Matcher
.\setup.ps1 -StartDev
```

### Linux/macOS (Bash)
```bash
git clone https://github.com/srbhr/Resume-Matcher.git
cd Resume-Matcher
chmod +x setup.sh
./setup.sh --start-dev
```

## 📊 Resource Requirements
- **Disk Space**: 10GB (includes AI model)
- **RAM**: 8GB minimum, 16GB recommended
- **Network**: Initial download ~3.5GB

## 🏗️ Architecture Overview
```
Frontend (Next.js 15 + React 19)  ←→  Backend (FastAPI + Python 3.12)
         ↓                                      ↓
    Port 3000                              Port 8000
                                              ↓
                                      Ollama AI Server
                                         (gemma3:4b)
                                              ↓
                                      SQLite Database
```

## 📝 Key Dependencies

### Backend Python Stack
- **FastAPI 0.115.12** - Web framework
- **SQLAlchemy 2.0.40** - Database ORM  
- **Ollama 0.4.7** - AI model integration
- **PDFMiner.six** - PDF processing
- **BeautifulSoup4** - HTML parsing

### Frontend JavaScript Stack  
- **Next.js 15.3.0** - React framework
- **React 19.0.0** - UI library
- **Tailwind CSS 4** - Styling
- **Radix UI** - Component primitives
- **TypeScript 5+** - Type safety

## ⚡ Quick Verification
After setup, verify everything works:
```bash
# Check services are running
curl http://localhost:8000/health  # Backend API
curl http://localhost:3000         # Frontend

# Check AI model
ollama list | grep gemma3
```

## 🔧 Common Issues
- **Port conflicts**: Ensure 3000 and 8000 are free
- **Memory issues**: Close other apps, need 8GB+ RAM
- **Network issues**: Large AI model download required
- **Permission issues**: Run setup scripts with proper permissions

For detailed troubleshooting, see [DEPENDENCIES.md](DEPENDENCIES.md)