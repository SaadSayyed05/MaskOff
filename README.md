# MaskOff: Neural-Powered Vision Intelligence

A sophisticated, futuristic face mask detection platform built with AI-powered YOLOv5/YOLOv8 object detection. Features real-time webcam streaming, image/video upload analysis, and a luxury-themed interface with professional UX design.

---

## 🎯 Project Overview

**MaskOff** is an intelligent mask detection system designed for security, automation, and compliance purposes. It leverages state-of-the-art computer vision to identify and classify face mask states across images, video streams, and live camera feeds.

### Key Capabilities
- **Real-time Detection** — Live webcam streaming with frame-by-frame analysis
- **Image Analysis** — Upload and analyze images with annotated results
- **Video Processing** — Batch video file analysis with aggregated statistics
- **Professional UI** — Luxury gold/dark theme with premium animations and effects
- **Responsive Design** — Works seamlessly across desktop and mobile devices
- **Legal Compliance** — Privacy Policy, Terms of Service, and detailed team information

---

## 📚 Tech Stack

### Frontend
- **React 18+** — Component-based UI library
- **React Router** — Client-side routing for multi-page navigation
- **Vite** — Lightning-fast build tool and dev server
- **CSS3** — Custom styling with luxury color palette and advanced animations
- **JavaScript ES6+** — Modern JavaScript features and async handling

### Backend
- **Python 3.8+** — Server-side programming language
- **FastAPI** — Modern, high-performance REST API framework
- **PyTorch** — Deep learning framework for model inference
- **YOLOv5/YOLOv8** — State-of-the-art object detection model
- **Uvicorn** — ASGI server for async request handling

### Architecture
- **Full-Stack Web Application** — Client-server architecture
- **REST API** — HTTP endpoints for image/video detection
- **WebSocket Streaming** — Real-time bidirectional communication for live detection
- **ML Model Inference** — On-device or server-side ML model execution

---

## 📁 Project Structure

```
face-mask-detection/
├── backend/
│   ├── main.py              ← FastAPI server with detection endpoints
│   ├── requirements.txt      ← Python dependencies
│   └── best.pt              ← YOLOv8 trained model weights
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx          ← Main router component
│   │   ├── App.css          ← Global styles (deprecated)
│   │   ├── index.css        ← Master stylesheet with luxury theme
│   │   ├── main.jsx         ← React entry point
│   │   ├── components/
│   │   │   ├── Navbar.jsx   ← Navigation header with top-right buttons
│   │   │   └── Footer.jsx   ← Site footer with legal links
│   │   └── pages/
│   │       ├── Home.jsx              ← Landing page with gradient title
│   │       ├── Detection.jsx         ← Live webcam detection
│   │       ├── ImageUpload.jsx       ← Image analysis interface
│   │       ├── VideoUpload.jsx       ← Video analysis interface
│   │       ├── About.jsx             ← Project information
│   │       ├── Contact.jsx           ← Team member profiles
│   │       ├── PrivacyPolicy.jsx     ← Privacy policy details
│   │       └── TermsOfService.jsx    ← Terms and conditions
│   │
│   ├── index.html           ← HTML template
│   ├── package.json         ← NPM dependencies and scripts
│   └── vite.config.js       ← Vite configuration
│
├── package.json             ← Root package configuration
└── README.md                ← Project documentation
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** 14+ with npm/yarn
- **Python** 3.8+ with pip
- **Git** for version control

### Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Ensure best.pt (YOLOv8 model) is in this directory
# If not available, download from Ultralytics: https://github.com/ultralytics/yolov8

# Start FastAPI server
python main.py
# Server running at http://localhost:8000
```

### Frontend Setup

```bash
cd frontend

# Install npm dependencies
npm install

# Start Vite development server
npm run dev
# Frontend running at http://localhost:5173

# Build for production
npm run build
```

---

## 🎨 Design System

### Color Palette
- **Primary Gold** — `#C9954C` (accent, highlights)
- **Gold Light** — `#E8B86D` (hover states, borders)
- **Dark Background** — `#111110` (main background)
- **Muted Accents** — Various earth tones for UI elements

### Animation Patterns
- **Springy Transitions** — Cubic-bezier easing `(0.34, 1.56, 0.64, 1)` for interactive feel
- **Ripple Effects** — Button click feedback with pseudo-element animations
- **Hover States** — Scale 1.02x on hover, 0.98x on click
- **Gradient Text** — Hero title with animated background clip effect

### Typography
- **Headers** — Bold, gradient-styled for emphasis
- **Body Text** — Clean, readable sans-serif
- **Labels** — Luxury aesthetic with subtle shadows

---

## 📋 Detection Classes

The model detects and classifies faces into 4 categories:

| Class | Description | Count |
|-------|-------------|-------|
| `masked` | Face with properly worn mask | Tracked |
| `unmasked` | Face without mask | Tracked |
| `improper` | Mask worn incorrectly | Tracked |
| `veil` | Face covered with veil | Tracked |

---

## 🔌 API Endpoints

### Backend Endpoints

| Method | Endpoint | Input | Output | Description |
|--------|----------|-------|--------|-------------|
| GET | `/` | — | JSON | Server info & available labels |
| GET | `/health` | — | JSON | Health check, model status |
| POST | `/detect/image` | Image file | JSON + Base64 | Analyze image, return annotated |
| POST | `/detect/video` | Video file | JSON | Analyze video, return frame counts |
| WS | `/ws/stream` | Binary frames | JSON | Real-time live camera detection |

### Response Format (Detection)

```json
{
  "detections": [
    {
      "class": "unmasked",
      "confidence": 0.95,
      "bbox": [x1, y1, x2, y2]
    }
  ],
  "counts": {
    "total": 5,
    "masked": 2,
    "unmasked": 2,
    "improper": 1,
    "veil": 0
  },
  "latency_ms": 120,
  "annotated_image": "base64_string_here"
}
```

---

## 🎯 Features

### Home Page
- **Futuristic Title** — "MaskOff: Neural-Powered Vision Intelligence" with gradient effect
- **Call-to-Action Buttons** — Quick links to detection features
- **Project Description** — Overview of capabilities and technology

### Live Detection (`/detection`)
- **Real-time Webcam Stream** — WebSocket-based frame capture and analysis
- **Detection Overlay** — Bounding boxes with class labels in real-time
- **Statistics Dashboard** — Live counters for each detection class
- **Latency Meter** — Displays inference time per frame
- **Professional Layout** — 1400px max-width optimized viewport

### Image Upload (`/upload`)
- **Drag-and-Drop Interface** — Or click to select image file
- **Instant Analysis** — Real-time detection processing
- **Annotated Results** — Bounding boxes overlay on original image
- **Detection Summary** — Total and per-class detection counts
- **Base64 Display** — Annotated image shown inline

### Video Upload (`/video`)
- **Video File Support** — MP4, AVI, MOV, WebM formats
- **Batch Processing** — Frame-by-frame video analysis
- **Aggregated Statistics** — Total and per-class counts across all frames
- **Performance Metrics** — Shows total frames processed and average latency
- **Clean Results Display** — Summary view without individual frame listings

### About Page (`/about`)
- **Project Mission** — Vision and goals of MaskOff
- **Technology Stack** — Complete list of frameworks and libraries
- **Model Details** — YOLOv8 architecture and training info
- **Use Cases** — Real-world applications

### Contact Page (`/contact`)
- **Team Member Profiles** — Roles and contact information
- **Professional Team Grid** — Vasundhara Yande, Abdul Rehman Khatib, Saad Syed
- **Email Links** — Direct contact to team members
- **No Scrolling Required** — Fits single viewport

### Legal Pages
- **Privacy Policy** (`/privacy`) — Data collection, processing, user rights (condensed)
- **Terms of Service** (`/terms`) — Usage agreements, liability, detection tool disclaimer (condensed)
- **Both pages fit single viewport** without scrolling

### Navigation & Footer
- **Top Navigation** — Navbar with logo and right-aligned navigation links
- **Responsive Menu** — Links: Home, Live Detection, Image, Video, About
- **Footer** — Copyright, links to Privacy Policy, Terms, and Contact
- **Professional Layout** — Consistent styling across all pages

---

## 🎬 Interactive Effects

- **Button Hover Effects** — Scale and brightness animations
- **Ripple Animation** — Click feedback on all buttons
- **Springy Transitions** — Smooth, engaging interactions
- **Title Glow** — Hero title with drop-shadow effects
- **Team Card Lift** — Hover animation lifts cards up 8px
- **Navbar Enhancement** — Backdrop blur and fixed positioning

---

## 🔒 Privacy & Compliance

- **Local Processing** — All image/video data stays on-device (configurable)
- **No Data Storage** — Images and videos not permanently stored
- **HTTPS Ready** — TLS/SSL encryption for data in transit
- **Privacy Policy** — Clear disclosure of data handling
- **Terms of Service** — Explicit liability disclaimers for detection tool

---

## 🛠️ Customization

### Change Color Scheme
Edit CSS variables in `frontend/src/index.css`:
```css
:root {
  --gold: #C9954C;
  --gold-light: #E8B86D;
  --dark-bg: #111110;
}
```

### Update Team Members
Edit `TEAM_MEMBERS` array in `frontend/src/pages/Contact.jsx`

### Modify Detection Classes
Update model class names in `backend/main.py` and frontend components

### Adjust Layout Widths
Search for `max-width` in `frontend/src/index.css` and modify pixel values

---

## 📊 Performance Metrics

- **Image Detection** — ~100-200ms per image (depends on model size)
- **Video Processing** — ~30-60ms per frame on modern hardware
- **Live Streaming** — ~10-15 FPS over WebSocket
- **Frontend Bundle** — ~150-200KB gzipped
- **Page Load Time** — <2 seconds on 4G connection

---

## 🤝 Team

- **Vasundhara Yande** — Dataset & Model Preparation Specialist
- **Abdul Rehman Khatib** — ML Model Architect & Validation Engineer
- **Saad Syed** — Full-Stack Platform Engineer

---

## 📝 License

This project is provided as-is for educational and commercial purposes. See [Terms of Service](/terms) for usage restrictions.

---

## 🚀 Future Enhancements

- Mobile app version (React Native)
- Multi-model support for different detection tasks
- Advanced analytics dashboard
- Export detection reports (PDF/CSV)
- Integration with security systems and APIs
- Edge deployment (Docker containerization)
- Performance optimization for lower-end devices
- Multi-language support

---

## ❓ Support

For questions, issues, or feedback, please contact the team through the [Contact Page](/contact) or email support directly.

**Happy detecting! 🎯**
