# TR-808 Step Sequencer

A browser-based TR-808 style step sequencer built with vanilla JavaScript and Web Audio API. No external libraries required.

## ✨ Features

### Core Functionality
- **16-step sequencer** with 3 classic drum tracks
- **Kick, Snare, Hi-Hat** synthesized with Web Audio API
- **Precise timing** using AudioContext scheduler (not setInterval)
- **BPM control** (60-200 BPM, default: 120)
- **Visual step highlighting** during playback

### Effects System
- **Reverb** - Convolver-based spatial effect with 2s decay
- **Delay** - Feedback delay synchronized to tempo (dotted 8th note)
- **Distortion** - WaveShaper with dynamic curve generation
- **Real-time control** - Adjust effects during playback

### User Experience
- **TR-808 inspired UI** - Gray base with orange accents
- **Responsive design** - Works on desktop and mobile
- **No installation** - Runs directly in the browser
- **Default pattern** - Demo pattern loaded on startup

## 🎮 Demo

[Live Demo](https://hfujikawa77.github.io/vc-sequencer/) *(Deploy to GitHub Pages first)*

## 🎵 Sound Design

All sounds are generated using Web Audio API nodes:

- **Kick**: Sine oscillator with pitch envelope (150Hz → 40Hz)
- **Snare**: White noise with highpass filter (1kHz) and short decay
- **Hi-Hat**: High-frequency noise (7kHz+) with very short envelope (50ms)

## 🚀 Quick Start

### Option 1: Open Locally
1. Clone this repository:
   ```bash
   git clone https://github.com/hfujikawa77/vc-sequencer.git
   cd vc-sequencer
   ```

2. Open `index.html` in your browser:
   ```bash
   open index.html
   # or
   python3 -m http.server 8000
   ```

### Option 2: Deploy to GitHub Pages
1. Go to your repository settings
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select:
   - **Branch**: `claude/tr808-step-sequencer-aoJiC` (or your main branch)
   - **Folder**: `/ (root)`
4. Click **Save**
5. Access your app at: `https://yourusername.github.io/vc-sequencer/`

## 🎛️ How to Use

### Basic Controls
1. **Play/Stop** - Start or stop the sequencer
2. **BPM** - Adjust tempo (60-200 BPM)
3. **Step Buttons** - Click to toggle steps ON/OFF
   - Orange = Active
   - Green border = Currently playing

### Effect Controls
- **Reverb** - Add spatial depth (0-100%)
- **Delay** - Create rhythmic echoes (0-100%)
- **Distortion** - Add warmth and punch (0-100%)

### Recommended Settings

**Trance**
```
Reverb: 60%
Delay: 40%
Distortion: 20%
```

**Lo-Fi**
```
Reverb: 10%
Delay: 50%
Distortion: 30%
```

**Clean**
```
Reverb: 20%
Delay: 0%
Distortion: 0%
```

## 🏗️ Technical Architecture

### Audio Signal Flow
```
Sound Generator → [Dry Signal] → Master Gain → Output
                ↘ [Reverb]     ↗
                ↘ [Delay]      ↗
                ↘ [Distortion] ↗
```

### Timing System
- Uses `AudioContext.currentTime` for sample-accurate scheduling
- Look-ahead scheduler checks every 25ms
- Schedules notes 100ms in advance
- No drift or timing issues compared to `setInterval`

### Effects Implementation
- **Reverb**: ConvolverNode with generated impulse response
- **Delay**: DelayNode with feedback loop (40% feedback)
- **Distortion**: WaveShaperNode with tanh-based transfer curve

## 📁 Project Structure

```
vc-sequencer/
├── index.html          # Complete single-file app
└── README.md          # This file
```

## 🛠️ Technology Stack

- **HTML5** - Structure
- **CSS3** - Styling with gradients and animations
- **Vanilla JavaScript** - No frameworks
- **Web Audio API** - Sound synthesis and effects
- **AudioContext** - Precise timing control

## 🎨 UI/UX Design

- **Color Scheme**: Dark gray base with orange (#ff6b35) accents
- **Typography**: Arial monospace for retro feel
- **Visual Feedback**:
  - Pulse animation on active steps
  - Glow effects on buttons and sliders
  - Color-coded track borders

## 🔧 Browser Compatibility

- ✅ Chrome 89+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 89+

*Requires Web Audio API support*

## 📝 Future Enhancements

- **Pattern Save/Load** - LocalStorage for multiple patterns
- **More Tracks** - Add Clap, Tom, Cymbal, etc.
- **Export Audio** - Record and download WAV files
- **MIDI Support** - External controller integration
- **Swing/Shuffle** - Humanize timing
- **Per-Track Effects** - Individual effect sends

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest features
- Submit pull requests

## 📄 License

MIT License - feel free to use this project for learning or commercial purposes.

## 🎵 Inspiration

Inspired by the legendary Roland TR-808 drum machine, this project demonstrates the power of the Web Audio API for creating musical instruments in the browser.

---

**Built with ❤️ using Web Audio API**

*No external libraries • Pure JavaScript • Open Source*
