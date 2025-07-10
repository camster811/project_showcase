# Oxide App - Binary Analysis & Visualization Tool

A sophisticated desktop application for binary analysis, reverse engineering, and malware research. Features advanced interactive visualizations, statistical analysis, and comprehensive disassembly capabilities built with modern web technologies and packaged as an Electron application.

## 🚀 Features

### Core Visualization Modules

- **Binary Visualizer** - Interactive grid-based visualization of raw binary data with color-coded byte values
- **Byte Histogram** - Statistical frequency analysis of byte distribution with logarithmic scaling
- **Byte N-grams Analysis** - Matrix-based heatmap visualization of byte sequence patterns
- **Call Graph Visualization** - Interactive network visualization of function call relationships
- **Control Flow Graph** - Advanced program flow analysis with function selector and interactive blocks
- **Entropy Analysis** - Statistical entropy analysis across memory addresses with detailed metrics
- **Opcode Histogram** - Assembly instruction frequency analysis with automatic scaling
- **Disassembly Differences** - Binary comparison and difference visualization tools

### Key Capabilities

- **Real-time Analysis** - Interactive tooltips, hover states, and dynamic data exploration
- **Export Functionality** - SVG and PNG export for all visualizations with custom backgrounds
- **Cross-platform** - Runs on Windows, macOS, and Linux via Electron
- **Modular Architecture** - Self-contained visualization components with independent data fetching
- **Advanced Algorithms** - Sophisticated graph layout algorithms (Dagre, force-directed positioning)
- **Statistical Analysis** - Entropy calculations, frequency distributions, n-gram analysis

## 🛠️ Technology Stack

### Frontend
- **Nuxt.js 3** - Vue.js framework with SSR capabilities
- **Vue 3 Composition API** - Reactive component architecture
- **TypeScript** - Type-safe development
- **PrimeVue** - Enterprise-grade UI component library
- **Tailwind CSS** - Utility-first CSS framework

### Visualization Libraries
- **D3.js** - Data-driven document manipulation for binary grids
- **Chart.js** - Responsive charts for histograms and line graphs
- **Cytoscape.js** - Graph theory library for control flow graphs
- **vis-network** - Network visualization for call graphs
- **chartjs-chart-matrix** - Matrix/heatmap chart extensions

### Desktop Integration
- **Electron** - Cross-platform desktop application framework
- **nuxt-electron** - Nuxt.js integration with Electron
- **electron-builder** - Application packaging and distribution

### Backend
- **Python API Server** - Binary analysis engine (Oxide-Formula)
- **RESTful API** - HTTP-based communication protocol
- **Binary Analysis Engine** - Core disassembly and analysis logic

## 📋 System Requirements

- Node.js 16+ and npm/yarn package manager
- Python 3.8+ for the analysis backend
- Modern web browser with WebGL support
- Minimum 4GB RAM for large binary analysis
- Graphics card with hardware acceleration recommended

## 🚀 Installation & Setup

### Development Environment

```bash
# Clone the repository
git clone https://github.com/yourusername/oxide-app.git
cd oxide-app

# Install dependencies
npm install
cd client && npm install

# Start development servers
./run.sh  # Starts both client and API server
```

### Building for Production

```bash
# Build the application
npm run build

# Package for distribution
npm run dist
```

### Manual Setup

```bash
# Start the client development server
cd client
npm run dev

# Start the Python API server (in separate terminal)
cd Oxide-Formula
source ./venv/Scripts/activate  # Windows
# source ./venv/bin/activate    # Linux/macOS
python3 main.py
```

## 🏗️ Project Structure

```
oxide-app/
├── client/                     # Nuxt.js frontend application
│   ├── components/            # Vue.js visualization components
│   │   ├── bytes_visualizer.vue
│   │   ├── byte_histogram.vue
│   │   ├── byte_ngrams.vue
│   │   ├── call_graph.vue
│   │   ├── control_flow_graph.vue
│   │   ├── EntropyChart.vue
│   │   ├── opcode_histogram.vue
│   │   └── LoadingSpinner.vue
│   ├── pages/                 # Application pages/routes
│   │   ├── index.vue
│   │   ├── binary_visualizer.vue
│   │   ├── chart_views.vue
│   │   ├── diff_view.vue
│   │   └── oxide_visuals.vue
│   ├── functions/             # Utility functions
│   ├── assets/               # CSS and static assets
│   └── nuxt.config.ts        # Nuxt.js configuration
├── Oxide-Formula/            # Python backend (referenced in run.sh)
├── package.json              # Electron dependencies
└── run.sh                    # Development startup script
```

## 🔧 Component Architecture

### Binary Visualizer Component
- **Technology**: D3.js + Canvas API
- **Features**: Interactive grid visualization, color-coded bytes, hover tooltips
- **Data Format**: 2D array of byte values
- **Export**: SVG with custom backgrounds

### Control Flow Graph Component
- **Technology**: Cytoscape.js + Dagre layout
- **Features**: Function selector, interactive blocks, dual-mode visualization
- **Data Format**: Nodes (basic blocks) and edges (control flow)
- **Algorithms**: Dagre hierarchical layout, force-directed positioning

### Call Graph Component
- **Technology**: vis-network
- **Features**: Hierarchical layouts, call count statistics, directed graphs
- **Data Format**: Function nodes with adjacency relationships
- **Layout**: Hierarchical with customizable node spacing

### Statistical Components
- **Histograms**: Chart.js with logarithmic/linear scaling
- **Entropy Analysis**: Line charts with PrimeVue data tables
- **N-grams**: Matrix heatmaps with chartjs-chart-matrix

## 🔌 API Integration

### Data Fetching Pattern
```javascript
const fetchDataAndPlot = async () => {
    const url = new URL("http://localhost:8000/api/retrieve");
    url.searchParams.append("selected_module", selectedModule);
    url.searchParams.append("selected_collection", selectedCollection);
    
    const response = await fetch(url);
    const data = await response.json();
    
    // Process and visualize data
    plotVisualization(data[oid]);
};
```

### Export Functionality
```javascript
const downloadChart = () => {
    const canvas = document.getElementById("chartCanvas");
    const tempCanvas = document.createElement("canvas");
    const tempCtx = tempCanvas.getContext("2d");
    
    // Apply dark background for better visibility
    tempCtx.fillStyle = "#333";
    tempCtx.fillRect(0, 0, tempCanvas.width, tempCanvas.height);
    tempCtx.drawImage(canvas, 0, 0);
    
    domtoimage.toSvg(tempCanvas)
        .then((dataUrl) => {
            const link = document.createElement("a");
            link.href = dataUrl;
            link.download = "analysis-chart.svg";
            link.click();
        });
};
```

## 🎯 Use Cases

### Security Research
- Malware analysis and reverse engineering
- Binary structure analysis and pattern recognition
- Encrypted/compressed section identification via entropy analysis

### Software Development
- Code optimization through opcode frequency analysis
- Control flow visualization for debugging
- Binary comparison for version analysis

### Academic Research
- Binary analysis algorithm development
- Visualization technique research
- Statistical analysis of executable formats

## 🔍 Advanced Features

### Graph Algorithms
- **Dagre Layout**: Hierarchical positioning for control flow graphs
- **Force-directed**: Dynamic node positioning for call graphs
- **Matrix Visualization**: Heatmap algorithms for n-gram analysis

### Statistical Analysis
- **Entropy Calculation**: Shannon entropy across memory addresses
- **Frequency Distribution**: Byte and opcode occurrence patterns
- **Pattern Recognition**: N-gram analysis for sequence identification

### Interactive Features
- **Real-time Tooltips**: Hover information for all visualizations
- **Dynamic Scaling**: Automatic logarithmic/linear scale switching
- **Function Navigation**: Interactive function selector for control flow graphs
- **Export Options**: Multiple format support with custom styling

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **D3.js** community for powerful data visualization capabilities
- **Vue.js** team for the reactive framework architecture
- **Electron** for cross-platform desktop application support
- **Chart.js** for comprehensive charting solutions
- **Cytoscape.js** for advanced graph visualization algorithms

## 📞 Support

For questions, issues, or contributions:
- Create an issue on GitHub
- Contact the development team
- Check the documentation wiki

---

**Oxide App** - Transforming binary analysis through advanced visualization
