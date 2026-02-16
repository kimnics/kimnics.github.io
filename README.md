<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Francis Mbugua | Web Developer & Security Researcher</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600;700&family=Orbitron:wght@700;900&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #00ff41;
            --secondary: #0f0;
            --dark: #0a0a0a;
            --darker: #050505;
            --accent: #00ffaa;
            --text: #e0e0e0;
            --glow: 0 0 20px rgba(0, 255, 65, 0.5);
        }

        body {
            font-family: 'Fira Code', monospace;
            background: var(--darker);
            color: var(--text);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Animated background grid */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 255, 65, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 65, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: grid-move 20s linear infinite;
            pointer-events: none;
            z-index: 0;
        }

        @keyframes grid-move {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        /* Cursor trail effect */
        .cursor-glow {
            position: fixed;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(0, 255, 65, 0.15) 0%, transparent 70%);
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 1;
            transition: opacity 0.3s;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative;
            z-index: 2;
        }

        /* Header */
        header {
            padding: 40px 0;
            border-bottom: 2px solid rgba(0, 255, 65, 0.2);
            position: relative;
        }

        .terminal-prompt {
            font-size: 14px;
            color: var(--primary);
            margin-bottom: 10px;
            opacity: 0;
            animation: fadeIn 0.5s forwards;
        }

        h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 4rem;
            font-weight: 900;
            color: var(--primary);
            text-shadow: var(--glow);
            margin-bottom: 10px;
            letter-spacing: 3px;
            opacity: 0;
            animation: glitchIn 1s forwards 0.3s;
        }

        .tagline {
            font-size: 1.2rem;
            color: var(--accent);
            margin-bottom: 20px;
            opacity: 0;
            animation: fadeIn 0.8s forwards 0.8s;
        }

        .typing-animation::after {
            content: '▊';
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        @keyframes glitchIn {
            0% {
                opacity: 0;
                transform: translateX(-20px);
                text-shadow: -5px 0 red, 5px 0 blue;
            }
            100% {
                opacity: 1;
                transform: translateX(0);
                text-shadow: var(--glow);
            }
        }

        /* Navigation */
        nav {
            margin-top: 30px;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 30px;
            flex-wrap: wrap;
        }

        nav a {
            color: var(--text);
            text-decoration: none;
            font-size: 14px;
            padding: 8px 16px;
            border: 1px solid rgba(0, 255, 65, 0.3);
            border-radius: 4px;
            transition: all 0.3s;
            display: inline-block;
        }

        nav a:hover {
            background: rgba(0, 255, 65, 0.1);
            border-color: var(--primary);
            box-shadow: var(--glow);
            transform: translateY(-2px);
        }

        /* Sections */
        section {
            padding: 80px 0;
            opacity: 0;
            animation: fadeIn 0.8s forwards;
            animation-delay: 1.2s;
        }

        h2 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 40px;
            position: relative;
            display: inline-block;
        }

        h2::before {
            content: '> ';
            color: var(--accent);
        }

        h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, var(--primary), transparent);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
        }

        .about-text p {
            margin-bottom: 20px;
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 30px;
        }

        .skill-tag {
            background: rgba(0, 255, 65, 0.1);
            border: 1px solid rgba(0, 255, 65, 0.3);
            padding: 8px 16px;
            border-radius: 4px;
            font-size: 14px;
            transition: all 0.3s;
        }

        .skill-tag:hover {
            background: rgba(0, 255, 65, 0.2);
            box-shadow: 0 0 15px rgba(0, 255, 65, 0.3);
            transform: scale(1.05);
        }

        .terminal-window {
            background: var(--dark);
            border: 2px solid rgba(0, 255, 65, 0.3);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        .terminal-header {
            background: rgba(0, 255, 65, 0.1);
            padding: 10px 15px;
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .terminal-button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--primary);
        }

        .terminal-body {
            padding: 20px;
            font-size: 14px;
            color: var(--primary);
        }

        .command-line {
            margin-bottom: 10px;
        }

        .command-line span {
            color: var(--accent);
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .project-card {
            background: var(--dark);
            border: 2px solid rgba(0, 255, 65, 0.2);
            border-radius: 8px;
            padding: 30px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
            transform: scaleX(0);
            transition: transform 0.3s;
        }

        .project-card:hover::before {
            transform: scaleX(1);
        }

        .project-card:hover {
            border-color: var(--primary);
            box-shadow: 0 10px 40px rgba(0, 255, 65, 0.2);
            transform: translateY(-5px);
        }

        .project-number {
            font-size: 3rem;
            font-family: 'Orbitron', sans-serif;
            color: rgba(0, 255, 65, 0.1);
            font-weight: 900;
            line-height: 1;
            margin-bottom: 10px;
        }

        .project-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            color: var(--primary);
            margin-bottom: 15px;
        }

        .project-card p {
            margin-bottom: 20px;
            color: var(--text);
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .project-tag {
            font-size: 12px;
            padding: 4px 10px;
            background: rgba(0, 255, 65, 0.1);
            border: 1px solid rgba(0, 255, 65, 0.3);
            border-radius: 3px;
        }

        .project-link {
            display: inline-block;
            color: var(--accent);
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
        }

        .project-link:hover {
            color: var(--primary);
            text-shadow: var(--glow);
        }

        /* Contact Section */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .contact-card {
            background: var(--dark);
            border: 2px solid rgba(0, 255, 65, 0.2);
            border-radius: 8px;
            padding: 30px;
            text-align: center;
            transition: all 0.3s;
        }

        .contact-card:hover {
            border-color: var(--primary);
            box-shadow: var(--glow);
            transform: translateY(-5px);
        }

        .contact-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .contact-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.2rem;
            color: var(--accent);
            margin-bottom: 10px;
        }

        .contact-card a {
            color: var(--text);
            text-decoration: none;
            transition: all 0.3s;
        }

        .contact-card a:hover {
            color: var(--primary);
            text-shadow: var(--glow);
        }

        /* Footer */
        footer {
            border-top: 2px solid rgba(0, 255, 65, 0.2);
            padding: 40px 0;
            text-align: center;
            margin-top: 80px;
        }

        footer p {
            color: rgba(255, 255, 255, 0.5);
            font-size: 14px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }

            h2 {
                font-size: 2rem;
            }

            .about-content {
                grid-template-columns: 1fr;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            nav ul {
                gap: 15px;
            }
        }

        /* Scroll reveal */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="cursor-glow" id="cursorGlow"></div>

    <div class="container">
        <header>
            <div class="terminal-prompt">francis@portfolio:~$ whoami</div>
            <h1>FRANCIS MBUGUA</h1>
            <p class="tagline typing-animation">Web Developer | Security Researcher | System Architect</p>
            
            <nav>
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#projects">Projects</a></li>
                    <li><a href="#contact">Contact</a></li>
                    <li><a href="https://github.com/kimnics" target="_blank">GitHub</a></li>
                </ul>
            </nav>
        </header>

        <section id="about">
            <h2>About Me</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>I'm a web developer and security researcher passionate about building robust, secure applications and exploring the depths of cybersecurity. I specialize in creating tools that enhance security testing and penetration testing capabilities.</p>
                    
                    <p>My work spans from full-stack web development to developing security research tools, with a focus on Python, JavaScript, and modern web technologies. I believe in writing clean, efficient code and continuously learning new techniques.</p>
                    
                    <div class="skills">
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">HTML/CSS</span>
                        <span class="skill-tag">React</span>
                        <span class="skill-tag">Node.js</span>
                        <span class="skill-tag">Security Testing</span>
                        <span class="skill-tag">Penetration Testing</span>
                        <span class="skill-tag">Linux</span>
                        <span class="skill-tag">Git</span>
                    </div>
                </div>

                <div class="terminal-window">
                    <div class="terminal-header">
                        <div class="terminal-button"></div>
                        <div class="terminal-button"></div>
                        <div class="terminal-button"></div>
                    </div>
                    <div class="terminal-body">
                        <div class="command-line"><span>$</span> cat skills.txt</div>
                        <div class="command-line">Loading modules...OK</div>
                        <div class="command-line">Initialization complete</div>
                        <div class="command-line">&nbsp;</div>
                        <div class="command-line">[+] Web Development</div>
                        <div class="command-line">[+] Security Research</div>
                        <div class="command-line">[+] Tool Development</div>
                        <div class="command-line">[+] System Architecture</div>
                        <div class="command-line">&nbsp;</div>
                        <div class="command-line"><span>$</span> status: ready_to_build</div>
                    </div>
                </div>
            </div>
        </section>

        <section id="projects">
            <h2>Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card reveal">
                    <div class="project-number">01</div>
                    <h3>RINGREAPER</h3>
                    <p>An advanced security research tool designed for network analysis and penetration testing. Features modular architecture for extensibility and comprehensive logging capabilities.</p>
                    <div class="project-tags">
                        <span class="project-tag">Python</span>
                        <span class="project-tag">Security</span>
                        <span class="project-tag">Networking</span>
                    </div>
                    <a href="#" class="project-link">View on GitHub →</a>
                </div>

                <div class="project-card reveal">
                    <div class="project-number">02</div>
                    <h3>Web Application Projects</h3>
                    <p>Collection of full-stack web applications built with modern frameworks. Features responsive design, RESTful APIs, and secure authentication systems.</p>
                    <div class="project-tags">
                        <span class="project-tag">React</span>
                        <span class="project-tag">Node.js</span>
                        <span class="project-tag">MongoDB</span>
                    </div>
                    <a href="#" class="project-link">Explore Projects →</a>
                </div>

                <div class="project-card reveal">
                    <div class="project-number">03</div>
                    <h3>Security Tools Suite</h3>
                    <p>A comprehensive suite of security testing tools for vulnerability assessment, including automated scanners and custom exploitation frameworks.</p>
                    <div class="project-tags">
                        <span class="project-tag">Python</span>
                        <span class="project-tag">Bash</span>
                        <span class="project-tag">Penetration Testing</span>
                    </div>
                    <a href="#" class="project-link">Learn More →</a>
                </div>
            </div>
        </section>

        <section id="contact">
            <h2>Get In Touch</h2>
            <div class="contact-grid">
                <div class="contact-card reveal">
                    <div class="contact-icon">📧</div>
                    <h3>Email</h3>
                    <a href="mailto:kimf7887@gmail.com">kimf7887@gmail.com</a>
                </div>

                <div class="contact-card reveal">
                    <div class="contact-icon">📱</div>
                    <h3>Phone</h3>
                    <a href="tel:0112136611">0112136611</a>
                </div>

                <div class="contact-card reveal">
                    <div class="contact-icon">💼</div>
                    <h3>LinkedIn</h3>
                    <a href="https://linkedin.com/in/francis-mbugua" target="_blank">@francis mbugua</a>
                </div>

                <div class="contact-card reveal">
                    <div class="contact-icon">🐙</div>
                    <h3>GitHub</h3>
                    <a href="https://github.com/kimnics" target="_blank">@kimnics</a>
                </div>

                <div class="contact-card reveal">
                    <div class="contact-icon">👤</div>
                    <h3>Facebook</h3>
                    <a href="https://facebook.com/francis.mbugua" target="_blank">francis mbugua</a>
                </div>
            </div>
        </section>

        <footer>
            <p>&copy; 2026 Francis Mbugua. Built with passion and code.</p>
            <p style="margin-top: 10px; font-size: 12px;">francis@portfolio:~$ █</p>
        </footer>
    </div>

    <script>
        // Cursor glow effect
        const cursorGlow = document.getElementById('cursorGlow');
        document.addEventListener('mousemove', (e) => {
            cursorGlow.style.left = e.clientX + 'px';
            cursorGlow.style.top = e.clientY + 'px';
        });

        // Scroll reveal animation
        const reveals = document.querySelectorAll('.reveal');
        
        function checkReveal() {
            reveals.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const windowHeight = window.innerHeight;
                
                if (elementTop < windowHeight - 100) {
                    element.classList.add('active');
                }
            });
        }

        window.addEventListener('scroll', checkReveal);
        checkReveal(); // Check on load

        // Smooth scrolling for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Console easter egg
        console.log('%c🔒 SECURITY NOTICE', 'color: #00ff41; font-size: 24px; font-weight: bold;');
        console.log('%cThis portfolio was built by Francis Mbugua', 'color: #00ffaa; font-size: 14px;');
        console.log('%cInterested in collaboration? Reach out: kimf7887@gmail.com', 'color: #0f0; font-size: 12px;');
    </script>
</body>
</html>
