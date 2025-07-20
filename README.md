# 🚗 ANPR - Automatic Number Plate Recognition System

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![React](https://img.shields.io/badge/React-18+-blue.svg)](https://reactjs.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.116+-green.svg)](https://fastapi.tiangolo.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0+-green.svg)](https://mongodb.com)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A comprehensive Automatic Number Plate Recognition (ANPR) system with advanced AI-powered detection, real-time analytics, and a modern web interface.

## ✨ Features

- 🔍 **Advanced Detection**: YOLOv8-based license plate detection with high accuracy
- 📸 **Image Processing**: Single image analysis with multi-plate detection
- 🎥 **Video Processing**: Multi-vehicle tracking with best frame selection
- 🤖 **Dual OCR**: Local YOLO OCR + Roboflow cloud OCR support
- 📊 **Real-time Analytics**: Live dashboard with performance metrics
- 🎨 **Modern UI**: Glassmorphic design with dark/light theme
- 📱 **Responsive**: Mobile-first responsive design
- 🔄 **Real-time Monitoring**: Backend health checks and status updates

## 🚀 Quick Start

### Prerequisites

- **Python 3.8+**
- **Node.js 16+**
- **MongoDB 7.0+**
- **Git**

### One-Command Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/ANPR_.git
cd ANPR_

# Make the startup script executable and run
chmod +x run_all.sh
./run_all.sh
```

This will automatically:

1. Start MongoDB service
2. Activate Python virtual environment
3. Start the FastAPI backend (port 8000)
4. Start the React frontend (port 5173)

### Manual Setup

#### Backend Setup

```bash
cd anpr-backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Start MongoDB (macOS)
brew services start mongodb-community@7.0

# Run backend
uvicorn app:app --reload
```

#### Frontend Setup

```bash
cd anpr-frontend/ANPR

# Install dependencies
npm install

# Start development server
npm run dev
```

## 📖 Usage

### 1. Image Processing

1. Navigate to `http://localhost:5173/image-processor`
2. Drag and drop or click to select an image
3. Click "Process" to analyze the image
4. View results with annotated images and OCR text

### 2. Video Processing

1. Navigate to `http://localhost:5173/video-processor`
2. Upload a video file
3. Wait for processing to complete
4. Review vehicle tracking results and best frame selections

### 3. Analytics Dashboard

1. Navigate to `http://localhost:5173/dashboard`
2. Monitor real-time system statistics
3. View performance metrics and recent detections
4. Check backend health status

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Backend      │    │    Database     │
│   (React)       │◄──►│   (FastAPI)     │◄──►│   (MongoDB)     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   UI Components │    │   AI Models     │    │   Detection     │
│   - Dashboard   │    │   - YOLO        │    │   Results       │
│   - Processors  │    │   - OCR         │    │   - Statistics  │
│   - Analytics   │    │   - Tracking    │    │   - History     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the `anpr-backend` directory:

```bash
# MongoDB Configuration
MONGODB_URI=mongodb://localhost:27017/anpr_db

# Roboflow OCR (Optional)
ROBOFLOW_API_KEY=your_api_key
ROBOFLOW_PROJECT=your_project
ROBOFLOW_VERSION=your_version
USE_ROBOFLOW_OCR=0  # Set to 1 to use Roboflow OCR

# Backend Configuration
HOST=0.0.0.0
PORT=8000
DEBUG=True
```

### Model Files

Ensure the following model files are present in `anpr-backend/models/`:

- `license_plate_detector.pt` - License plate detection model
- `character_detector.pt` - Character recognition model

## 📊 API Endpoints

| Endpoint                    | Method | Description           |
| --------------------------- | ------ | --------------------- |
| `/`                         | GET    | Health check          |
| `/api/v1/process-image`     | POST   | Process single image  |
| `/api/v1/process-video`     | POST   | Process video file    |
| `/api/v1/stats`             | GET    | Get system statistics |
| `/api/v1/recent-detections` | GET    | Get recent detections |

## 🛠️ Development

### Project Structure

```
ANPR_/
├── anpr-backend/           # FastAPI backend
│   ├── app.py             # Main application
│   ├── image_ocr.py       # Image processing
│   ├── video_ocr.py       # Video processing
│   ├── roboflow_ocr.py    # Cloud OCR integration
│   ├── models/            # AI model files
│   ├── results/           # Generated results
│   └── requirements.txt   # Python dependencies
├── anpr-frontend/         # React frontend
│   └── ANPR/
│       ├── src/
│       │   ├── pages/     # Main components
│       │   ├── components/# UI components
│       │   └── App.jsx    # Main app
│       └── package.json   # Node dependencies
├── run_all.sh            # Startup script
├── requirements.txt      # Root dependencies
└── README.md            # This file
```

### Running Tests

```bash
# Backend tests
cd anpr-backend
python -m pytest

# Frontend tests
cd anpr-frontend/ANPR
npm test
```

## 🚨 Troubleshooting

### Common Issues

**Backend won't start:**

- Check MongoDB is running: `brew services list | grep mongodb`
- Verify port 8000 is available: `lsof -i :8000`
- Check Python dependencies: `pip list`

**Frontend connection issues:**

- Ensure backend is running on port 8000
- Check CORS configuration in backend
- Verify network connectivity

**Model loading errors:**

- Ensure model files exist in `models/` directory
- Check file permissions
- Verify model file integrity

**OCR failures:**

- Check image quality and lighting
- Verify license plate visibility
- Review OCR configuration settings

## 📈 Performance

- **Image Processing**: ~200-500ms per image
- **Video Processing**: ~2-5 seconds per second of video
- **Detection Accuracy**: 95%+ on clear images
- **OCR Accuracy**: 90%+ on well-lit plates

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards

- Follow PEP 8 for Python code
- Use ESLint for JavaScript/React
- Write comprehensive tests
- Update documentation

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Ultralytics](https://ultralytics.com/) for YOLOv8
- [Roboflow](https://roboflow.com/) for cloud OCR
- [FastAPI](https://fastapi.tiangolo.com/) for the backend framework
- [React](https://reactjs.org/) for the frontend framework
- [Tailwind CSS](https://tailwindcss.com/) for styling

## 📞 Support

- 📧 Email: support@anpr-system.com
- 🐛 Issues: [GitHub Issues](https://github.com/yourusername/ANPR_/issues)
- 📖 Documentation: [Full Documentation](DOCUMENTATION.md)

---

<div align="center">
  <p>Made with ❤️ by the ANPR Team</p>
  <p>
    <a href="https://github.com/yourusername/ANPR_/stargazers">
      <img src="https://img.shields.io/github/stars/yourusername/ANPR_" alt="Stars">
    </a>
    <a href="https://github.com/yourusername/ANPR_/network">
      <img src="https://img.shields.io/github/forks/yourusername/ANPR_" alt="Forks">
    </a>
    <a href="https://github.com/yourusername/ANPR_/issues">
      <img src="https://img.shields.io/github/issues/yourusername/ANPR_" alt="Issues">
    </a>
  </p>
</div>
