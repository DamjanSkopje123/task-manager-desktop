<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task Manager Desktop - OPTIMUM CREATIVE SOLUTIONS</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0a0a0a;
            color: white;
            overflow-x: hidden;
        }

        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .content {
            position: relative;
            z-index: 10;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 2rem;
        }

        .logo {
            font-size: 4rem;
            font-weight: bold;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb, #f5576c);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .company-name {
            font-size: 1.5rem;
            color: #667eea;
            margin-bottom: 2rem;
            font-weight: 300;
            letter-spacing: 2px;
        }

        .app-title {
            font-size: 3rem;
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .app-subtitle {
            font-size: 1.2rem;
            color: #ccc;
            margin-bottom: 3rem;
            max-width: 600px;
        }

        .download-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 20px 40px;
            text-decoration: none;
            border-radius: 50px;
            font-size: 1.3rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
            position: relative;
            overflow: hidden;
        }

        .download-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        .download-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .download-btn:hover::before {
            left: 100%;
        }

        .features {
            margin-top: 4rem;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            width: 100%;
        }

        .feature {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
        }

        .feature:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.1);
        }

        .feature-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .feature-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .feature-desc {
            color: #ccc;
            line-height: 1.6;
        }

        .floating-shapes {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 5;
        }

        .shape {
            position: absolute;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }

        .shape:nth-child(1) { animation-delay: 0s; }
        .shape:nth-child(2) { animation-delay: 2s; }
        .shape:nth-child(3) { animation-delay: 4s; }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        .stats {
            margin-top: 3rem;
            display: flex;
            gap: 2rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .stat {
            text-align: center;
            padding: 1rem;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #667eea;
        }

        .stat-label {
            color: #ccc;
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            .logo { font-size: 2.5rem; }
            .app-title { font-size: 2rem; }
            .features { grid-template-columns: 1fr; }
            .stats { flex-direction: column; }
        }
    </style>
</head>
<body>
    <div id="canvas-container"></div>
    
    <div class="floating-shapes">
        <div class="shape" style="top: 10%; left: 10%; font-size: 3rem;">🚀</div>
        <div class="shape" style="top: 20%; right: 15%; font-size: 2.5rem;">✨</div>
        <div class="shape" style="bottom: 30%; left: 20%; font-size: 2rem;">🎯</div>
        <div class="shape" style="bottom: 20%; right: 10%; font-size: 2.5rem;">💎</div>
    </div>

    <div class="content">
        <div class="logo">🚀</div>
        <div class="company-name">OPTIMUM CREATIVE SOLUTIONS</div>
        <h1 class="app-title">Task Manager Desktop</h1>
        <p class="app-subtitle">
            Professional desktop task management application with stunning 3D animations, 
            smooth performance, and enterprise-grade features. Built for productivity.
        </p>
        
        <a href="TaskManager-Installer.zip" class="download-btn" download>
            📥 Download Now
        </a>

        <div class="stats">
            <div class="stat">
                <div class="stat-number">20KB</div>
                <div class="stat-label">Lightweight</div>
            </div>
            <div class="stat">
                <div class="stat-number">60fps</div>
                <div class="stat-label">Smooth Animations</div>
            </div>
            <div class="stat">
                <div class="stat-number">AES-256</div>
                <div class="stat-label">Encrypted</div>
            </div>
            <div class="stat">
                <div class="stat-number">Auto</div>
                <div class="stat-label">Updates</div>
            </div>
        </div>

        <div class="features">
            <div class="feature">
                <div class="feature-icon">🎯</div>
                <div class="feature-title">Smart Task Management</div>
                <div class="feature-desc">Create, edit, and organize tasks with intelligent prioritization and beautiful 3D animations.</div>
            </div>
            <div class="feature">
                <div class="feature-icon">🔒</div>
                <div class="feature-title">Enterprise Security</div>
                <div class="feature-desc">AES-256 encryption, secure IPC, and comprehensive input validation for maximum protection.</div>
            </div>
            <div class="feature">
                <div class="feature-icon">🎨</div>
                <div class="feature-title">Stunning UI/UX</div>
                <div class="feature-desc">Modern design with smooth 60fps animations, dark/light themes, and responsive layout.</div>
            </div>
            <div class="feature">
                <div class="feature-icon">⚡</div>
                <div class="feature-title">Lightning Fast</div>
                <div class="feature-desc">Starts in under 1.5 seconds with optimized performance and minimal resource usage.</div>
            </div>
            <div class="feature">
                <div class="feature-icon">🔄</div>
                <div class="feature-title">Auto Updates</div>
                <div class="feature-desc">Silent background updates with professional notifications and safe rollback protection.</div>
            </div>
            <div class="feature">
                <div class="feature-icon">💎</div>
                <div class="feature-title">Professional Grade</div>
                <div class="feature-desc">Commercial-quality software that rivals Todoist, Microsoft To-Do, and Any.do.</div>
            </div>
        </div>
    </div>

    <script>
        // Three.js 3D Animation
        let scene, camera, renderer, particles;

        function init() {
            scene = new THREE.Scene();
            camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
            renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setClearColor(0x000000, 0);
            document.getElementById('canvas-container').appendChild(renderer.domElement);

            // Create floating geometric shapes
            const geometry = new THREE.IcosahedronGeometry(1, 0);
            const material = new THREE.MeshBasicMaterial({ 
                color: 0x667eea, 
                wireframe: true,
                transparent: true,
                opacity: 0.3
            });

            particles = [];
            for (let i = 0; i < 50; i++) {
                const particle = new THREE.Mesh(geometry, material);
                particle.position.set(
                    (Math.random() - 0.5) * 20,
                    (Math.random() - 0.5) * 20,
                    (Math.random() - 0.5) * 20
                );
                particle.rotation.set(
                    Math.random() * Math.PI,
                    Math.random() * Math.PI,
                    Math.random() * Math.PI
                );
                particle.scale.setScalar(Math.random() * 0.5 + 0.5);
                particles.push(particle);
                scene.add(particle);
            }

            camera.position.z = 10;
        }

        function animate() {
            requestAnimationFrame(animate);

            // Rotate particles
            particles.forEach((particle, index) => {
                particle.rotation.x += 0.01;
                particle.rotation.y += 0.01;
                particle.position.y += Math.sin(Date.now() * 0.001 + index) * 0.01;
                particle.position.x += Math.cos(Date.now() * 0.001 + index) * 0.01;
            });

            renderer.render(scene, camera);
        }

        function onWindowResize() {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        }

        // Initialize and start animation
        init();
        animate();
        window.addEventListener('resize', onWindowResize);

        // Add smooth scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe features for animation
        document.querySelectorAll('.feature').forEach(feature => {
            feature.style.opacity = '0';
            feature.style.transform = 'translateY(30px)';
            feature.style.transition = 'all 0.6s ease';
            observer.observe(feature);
        });

        // Add download button animation
        const downloadBtn = document.querySelector('.download-btn');
        downloadBtn.addEventListener('mouseenter', () => {
            downloadBtn.style.transform = 'translateY(-3px) scale(1.05)';
        });
        downloadBtn.addEventListener('mouseleave', () => {
            downloadBtn.style.transform = 'translateY(0) scale(1)';
        });
    </script>
</body>
</html> 
