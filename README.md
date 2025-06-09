<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hippocratic AI Case Study: 1,000-Person Tournament</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
            color: #334155;
            overflow-x: hidden;
        }
        
        .presentation-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .slide {
            background: white;
            min-height: 800px;
            margin-bottom: 40px;
            border-radius: 16px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.15);
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }
        
        /* Title Page */
        .title-slide {
            background: linear-gradient(135deg, #6366F1 0%, #8B5CF6 50%, #EC4899 100%);
            color: white;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
        }
        
        .hippocratic-logo {
            position: absolute;
            top: 40px;
            left: 40px;
            font-size: 20px;
            font-weight: bold;
            color: white;
            z-index: 10;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo-svg {
            width: 40px;
            height: 40px;
        }
        
        .tic-tac-toe-pattern {
            position: absolute;
            top: 40px;
            right: 40px;
            width: 60px;
            height: 60px;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 4px;
            z-index: 10;
        }
        
        .tic-square {
            background: rgba(255,255,255,0.2);
            border-radius: 4px;
        }
        
        .main-title {
            font-size: 48px;
            font-weight: bold;
            margin-bottom: 20px;
            z-index: 10;
            position: relative;
        }
        
        .case-study-subtitle {
            font-size: 28px;
            margin-bottom: 40px;
            opacity: 0.9;
            z-index: 10;
            position: relative;
        }
        
        .author-info {
            font-size: 20px;
            opacity: 0.8;
            z-index: 10;
            position: relative;
        }
        
        /* Regular slides */
        .slide-header {
            background: linear-gradient(135deg, #1E293B 0%, #475569 100%);
            color: white;
            padding: 30px 40px;
            position: relative;
        }
        
        .slide-number {
            position: absolute;
            top: 20px;
            right: 30px;
            background: rgba(255,255,255,0.2);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: bold;
        }
        
        .slide-title {
            font-size: 36px;
            font-weight: bold;
            line-height: 1.2;
        }
        
        .slide-content {
            flex: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
        }
        
        /* Content grids and sections */
        .content-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin: 20px 0;
        }
        
        .content-section {
            background: #F8FAFC;
            padding: 25px;
            border-radius: 12px;
            border-left: 4px solid #6366F1;
        }
        
        .section-title {
            color: #1E293B;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .bullet-point {
            display: flex;
            align-items: flex-start;
            margin-bottom: 12px;
            font-size: 14px;
            line-height: 1.4;
        }
        
        .bullet-icon {
            background: #10B981;
            color: white;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            font-size: 10px;
            font-weight: bold;
            flex-shrink: 0;
            margin-top: 1px;
        }
        
        /* Dashboard metrics */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .metric-card {
            background: linear-gradient(135deg, #F8FAFC 0%, #F1F5F9 100%);
            border: 2px solid #E2E8F0;
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }
        
        .metric-card:hover {
            transform: translateY(-4px);
        }
        
        .metric-value {
            color: #1E293B;
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 8px;
        }
        
        .metric-label {
            color: #64748B;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            font-weight: 600;
        }
        
        .ticker-style {
            background: linear-gradient(90deg, #10B981 0%, #059669 100%);
            color: white;
            padding: 15px;
            overflow: hidden;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .ticker-content {
            font-weight: bold;
            font-size: 14px;
            animation: scroll 15s linear infinite;
            white-space: nowrap;
        }
        
        @keyframes scroll {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }
        
        /* Bracket flow */
        .bracket-flow {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 30px 0;
            padding: 30px;
            background: linear-gradient(135deg, #F8FAFC 0%, #E2E8F0 100%);
            border-radius: 16px;
            border: 2px solid #CBD5E1;
        }
        
        .bracket-stage {
            text-align: center;
            flex: 1;
        }
        
        .bracket-number {
            background: linear-gradient(135deg, #6366F1 0%, #8B5CF6 100%);
            color: white;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 24px;
            margin: 0 auto 15px;
            box-shadow: 0 8px 20px rgba(99, 102, 241, 0.3);
        }
        
        .bracket-label {
            font-size: 16px;
            font-weight: bold;
            color: #1E293B;
            margin-bottom: 5px;
        }
        
        .bracket-detail {
            font-size: 12px;
            color: #64748B;
        }
        
        .bracket-arrow {
            color: #10B981;
            font-size: 32px;
            margin: 0 20px;
            font-weight: bold;
        }
        
        /* Schedule grid */
        .schedule-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin: 30px 0;
        }
        
        .schedule-block {
            background: white;
            border: 2px solid #E2E8F0;
            border-radius: 12px;
            padding: 15px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        .schedule-time {
            color: #6366F1;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 8px;
        }
        
        .schedule-event {
            color: #1E293B;
            font-size: 13px;
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .schedule-detail {
            color: #64748B;
            font-size: 11px;
        }
        
        /* Tech integration */
        .tech-integration {
            background: linear-gradient(135deg, #EEF2FF 0%, #E0E7FF 100%);
            border: 2px solid #6366F1;
            padding: 25px;
            border-radius: 12px;
            margin-top: 30px;
        }
        
        .tech-title {
            color: #1E293B;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            text-align: center;
        }
        
        .tech-features {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
        }
        
        .tech-tag {
            background: white;
            border: 1px solid #C7D2FE;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 12px;
            color: #1E293B;
            font-weight: 500;
        }
        
        /* Site map visual */
        .site-map {
            background: linear-gradient(135deg, #F8FAFC 0%, #F1F5F9 100%);
            border: 2px solid #E2E8F0;
            border-radius: 16px;
            padding: 40px;
            position: relative;
            min-height: 500px;
            overflow: hidden;
        }
        
        .map-zone {
            position: absolute;
            border: 3px solid;
            border-radius: 12px;
            padding: 15px;
            font-size: 11px;
            font-weight: bold;
            text-align: center;
            background: rgba(255,255,255,0.95);
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        .competition-zone {
            top: 80px;
            left: 200px;
            width: 280px;
            height: 180px;
            border-color: #EF4444;
            color: #EF4444;
        }
        
        .participant-hub {
            top: 80px;
            left: 50px;
            width: 120px;
            height: 120px;
            border-color: #3B82F6;
            color: #3B82F6;
        }
        
        .command-center {
            top: 220px;
            left: 50px;
            width: 120px;
            height: 100px;
            border-color: #10B981;
            color: #10B981;
        }
        
        .food-area {
            top: 280px;
            left: 200px;
            width: 140px;
            height: 80px;
            border-color: #F59E0B;
            color: #F59E0B;
        }
        
        .accessibility-path {
            top: 280px;
            left: 360px;
            width: 120px;
            height: 80px;
            border-color: #8B5CF6;
            color: #8B5CF6;
        }
        
        /* Risk mitigation */
        .mitigation-strategies {
            background: white;
            border: 2px solid #E2E8F0;
            border-radius: 12px;
            padding: 25px;
            max-height: 500px;
            overflow-y: auto;
        }
        
        .mitigation-title {
            color: #1E293B;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 20px;
            text-align: center;
        }
        
        .mitigation-item {
            margin-bottom: 12px;
            padding: 10px;
            background: #F8FAFC;
            border-radius: 8px;
            border-left: 4px solid #10B981;
        }
        
        .mitigation-risk {
            font-size: 13px;
            font-weight: bold;
            color: #1E293B;
            margin-bottom: 4px;
        }
        
        .mitigation-action {
            font-size: 11px;
            color: #64748B;
            line-height: 1.3;
        }
        
        /* Risk matrix */
        .risk-matrix-wrapper {
            position: relative;
            background: white;
            border: 2px solid #E2E8F0;
            border-radius: 12px;
            padding: 30px;
        }
        
        .risk-matrix {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            grid-template-rows: repeat(2, 1fr);
            gap: 15px;
            margin-top: 20px;
        }
        
        .risk-cell {
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            font-size: 14px;
            font-weight: bold;
            border: 2px solid;
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .risk-high-high {
            background: #FEE2E2;
            border-color: #DC2626;
            color: #DC2626;
        }
        
        .risk-high-low {
            background: #FEF3C7;
            border-color: #D97706;
            color: #D97706;
        }
        
        .risk-low-high {
            background: #DBEAFE;
            border-color: #2563EB;
            color: #2563EB;
        }
        
        .risk-low-low {
            background: #D1FAE5;
            border-color: #059669;
            color: #059669;
        }
        
        /* Change management story flow */
        .change-story {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 25px;
            margin: 20px 0;
        }
        
        .story-card {
            background: white;
            border: 2px solid #E2E8F0;
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        .story-icon {
            font-size: 32px;
            margin-bottom: 15px;
        }
        
        .story-title {
            color: #1E293B;
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .story-content {
            color: #64748B;
            font-size: 12px;
            line-height: 1.4;
        }
        
        /* Gantt chart styles */
        .gantt-container {
            background: #F8FAFC;
            border: 2px solid #E2E8F0;
            border-radius: 16px;
            padding: 30px;
            margin: 20px 0;
            overflow-x: auto;
        }
        
        .gantt-header {
            display: grid;
            grid-template-columns: 220px repeat(24, 1fr);
            gap: 2px;
            margin-bottom: 15px;
        }
        
        .gantt-week {
            background: #1E293B;
            color: white;
            padding: 8px 4px;
            text-align: center;
            font-size: 10px;
            font-weight: bold;
            border-radius: 4px;
        }
        
        .gantt-row {
            display: grid;
            grid-template-columns: 220px repeat(24, 1fr);
            gap: 2px;
            margin-bottom: 8px;
            align-items: center;
        }
        
        .gantt-task {
            background: #E2E8F0;
            padding: 12px;
            font-size: 13px;
            font-weight: bold;
            color: #1E293B;
            border-radius: 6px;
        }
        
        .gantt-bar {
            height: 35px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 10px;
            font-weight: bold;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .phase-discovery { background: linear-gradient(135deg, #6366F1 0%, #8B5CF6 100%); }
        .phase-design { background: linear-gradient(135deg, #3B82F6 0%, #1D4ED8 100%); }
        .phase-pilot { background: linear-gradient(135deg, #EF4444 0%, #DC2626 100%); }
        .phase-prep { background: linear-gradient(135deg, #10B981 0%, #059669 100%); }
        .phase-event { background: linear-gradient(135deg, #F59E0B 0%, #D97706 100%); }
        .phase-analysis { background: linear-gradient(135deg, #8B5CF6 0%, #7C3AED 100%); }
        
        .highlight-box {
            background: linear-gradient(135deg, #EEF2FF 0%, #E0E7FF 100%);
            border: 2px solid #6366F1;
            padding: 25px;
            border-radius: 12px;
            margin: 20px 0;
            text-align: center;
        }
        
        .highlight-title {
            color: #1E293B;
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 15px;
        }
    </style>
</head>
<body>
    <div class="presentation-container">
        
        <!-- TITLE PAGE -->
        <div class="slide title-slide">
            <div class="hippocratic-logo">
                <div>
                    <div style="font-size: 20px;">Hippocratic AI</div>
                    <div style="font-size: 12px; opacity: 0.8;">— Do No Harm —</div>
                </div>
            </div>
            <div class="tic-tac-toe-pattern">
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
                <div class="tic-square"></div>
            </div>
            
            <div class="main-title">1,000-Person Tournament</div>
            <div class="case-study-subtitle">Customer Success Case Study</div>
            <div class="author-info">Presented by Shweta Gohil</div>
        </div>

        <!-- SLIDE 1: Goals & Definition of Success -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">01</div>
                <div class="slide-title">Goals & Definition of Success</div>
            </div>
            <div class="slide-content">
                <div class="content-grid">
                    <div class="content-section">
                        <div class="section-title">Primary Objectives</div>
                        <div class="bullet-point">
                            <div class="bullet-icon">✓</div>
                            <div><strong>Customer Experience:</strong> 95%+ satisfaction & engagement</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">✓</div>
                            <div><strong>Operational Excellence:</strong> Zero safety incidents, <5% delays</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">✓</div>
                            <div><strong>Community Impact:</strong> $50K+ for local charity</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">✓</div>
                            <div><strong>Sponsor ROI:</strong> Measurable brand engagement & visibility</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">✓</div>
                            <div><strong>Scalability:</strong> Replicable framework development</div>
                        </div>
                    </div>
                    
                    <div class="content-section">
                        <div class="section-title">Success by Stakeholder</div>
                        <div class="bullet-point">
                            <div class="bullet-icon">👥</div>
                            <div><strong>Participants:</strong> "Exceeded expectations; highly recommend"</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🤝</div>
                            <div><strong>Sponsors:</strong> "Increased inbound and brand engagement"</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🏘️</div>
                            <div><strong>Community:</strong> "Positive impact with zero disruption"</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">⚙️</div>
                            <div><strong>Internal Team:</strong> "Replicable framework with best practices"</div>
                        </div>
                    </div>
                </div>
                
                <div class="dashboard-grid">
                    <div class="metric-card">
                        <div class="metric-value">94.2%</div>
                        <div class="metric-label">Engagement Rate</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-value">2.4 min</div>
                        <div class="metric-label">Check-in Time</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-value">0.3%</div>
                        <div class="metric-label">Escalation Incidents</div>
                    </div>
                    <div class="metric-card ticker-style">
                        <div class="ticker-content">💰 Goal: $50,000 for Local Charity • Current: $47,350 • 94.7% Complete 💰</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SLIDE 2: Tournament Design & Structure -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">02</div>
                <div class="slide-title">Tournament Design & Structure</div>
            </div>
            <div class="slide-content">
                <!-- Bracket Progression -->
                <div class="bracket-flow">
                    <div class="bracket-stage">
                        <div class="bracket-number">1000</div>
                        <div class="bracket-label">Virtual Registration</div>
                        <div class="bracket-detail">10 games each online</div>
                    </div>
                    <div class="bracket-arrow">→</div>
                    <div class="bracket-stage">
                        <div class="bracket-number">200</div>
                        <div class="bracket-label">Live Finalists</div>
                        <div class="bracket-detail">Top performers qualify</div>
                    </div>
                    <div class="bracket-arrow">→</div>
                    <div class="bracket-stage">
                        <div class="bracket-number">1</div>
                        <div class="bracket-label">Champion</div>
                        <div class="bracket-detail">Single elimination</div>
                    </div>
                </div>
                
                <!-- Day-of Schedule -->
                <div class="schedule-grid">
                    <div class="schedule-block">
                        <div class="schedule-time">6:00 AM</div>
                        <div class="schedule-event">Site Setup Begins</div>
                        <div class="schedule-detail">4-hour window, simultaneous teams</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">8:00 AM</div>
                        <div class="schedule-event">Technology Testing & Calibration</div>
                        <div class="schedule-detail">Including AI agent system validation</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">9:00 AM</div>
                        <div class="schedule-event">Staff & Volunteer Briefing</div>
                        <div class="schedule-detail">Final preparations and run-throughs</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">10:00 AM</div>
                        <div class="schedule-event">Finalist Check-in Opens</div>
                        <div class="schedule-detail">AI-accelerated processing</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">11:00 AM</div>
                        <div class="schedule-event">Opening Ceremony & Round 1</div>
                        <div class="schedule-detail">200→100 elimination begins</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">12:00 PM</div>
                        <div class="schedule-event">Round 2 Begins</div>
                        <div class="schedule-detail">100→50 participants</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">1:00 PM</div>
                        <div class="schedule-event">Lunch Break & Round 3</div>
                        <div class="schedule-detail">Staggered for continuous play, 50→25</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">2:30 PM</div>
                        <div class="schedule-event">Round 4 (25→12)</div>
                        <div class="schedule-detail">Featured court commentary begins</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">3:30 PM</div>
                        <div class="schedule-event">Round 5 (12→6)</div>
                        <div class="schedule-detail">Semi-finalist determination</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">4:00 PM</div>
                        <div class="schedule-event">Championship Rounds</div>
                        <div class="schedule-detail">6→3→Champion finals</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">5:30 PM</div>
                        <div class="schedule-event">Awards Ceremony</div>
                        <div class="schedule-detail">Event wrap-up and recognition</div>
                    </div>
                    <div class="schedule-block">
                        <div class="schedule-time">6:00 PM</div>
                        <div class="schedule-event">Site Breakdown Begins</div>
                        <div class="schedule-detail">Equipment breakdown and cleanup</div>
                    </div>
                </div>
                
                <!-- Technology Integration -->
                <div class="tech-integration">
                    <div class="tech-title">⚡ Technology Integration Throughout Event Day</div>
                    <div class="tech-features">
                        <div class="tech-tag">Real-time bracket updates</div>
                        <div class="tech-tag">AI-powered matchmaking</div>
                        <div class="tech-tag">Predictive wait times</div>
                        <div class="tech-tag">QR code profiles</div>
                        <div class="tech-tag">Live leaderboards</div>
                        <div class="tech-tag">Automated notifications</div>
                        <div class="tech-tag">Hippocratic AI agent support</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SLIDE 3: Site Layout & Logistics -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">03</div>
                <div class="slide-title">Site Layout & Logistics</div>
            </div>
            <div class="slide-content">
                <div class="content-grid">
                    <div class="site-map">
                        <div class="map-zone participant-hub">
                            <div>PARTICIPANT HUB</div>
                            <div style="font-size: 10px; margin-top: 8px;">
                                • AI Check-in < 3min<br>
                                • Lounge & Waiting Area<br>
                                • Medical Station<br>
                                • Information Desk
                            </div>
                        </div>
                        
                        <div class="map-zone competition-zone">
                            <div>COMPETITION ZONE</div>
                            <div style="font-size: 10px; margin-top: 8px;">
                                • 20 Modular Courts (10'x10')<br>
                                • Professional Lighting<br>
                                • Live Commentary Booth<br>
                                • 1:2 Court Coverage Ratio<br>
                                • Weather-resistant Materials
                            </div>
                        </div>
                        
                        <div class="map-zone command-center">
                            <div>COMMAND CENTER</div>
                            <div style="font-size: 10px; margin-top: 8px;">
                                • Real-time Coordination<br>
                                • Equipment Storage<br>
                                • Technical Support<br>
                                • Backup Systems
                            </div>
                        </div>
                        
                        <div class="map-zone food-area">
                            <div>FOOD & BEVERAGE</div>
                            <div style="font-size: 10px; margin-top: 8px;">
                                • Local Food Trucks<br>
                                • Hydration Stations<br>
                                • Pre-ordering App
                            </div>
                        </div>
                        
                        <div class="map-zone accessibility-path">
                            <div>ACCESSIBILITY ZONE</div>
                            <div style="font-size: 10px; margin-top: 8px;">
                                • ADA Pathways<br>
                                • Viewing Areas<br>
                                • Assistance Available<br>
                                • Reserved Parking
                            </div>
                        </div>
                    </div>
                    
                    <div class="content-section">
                        <div class="section-title">Staffing & Resource Allocation</div>
                        <div class="bullet-point">
                            <div class="bullet-icon">⚖️</div>
                            <div><strong>Tournament Officials:</strong> 20 (1/court + backups) for fair play and swift issue resolution</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🤖</div>
                            <div><strong>On-site AI Support Specialists:</strong> 5 (Human Oversight) - Dedicated staff to monitor AI agent performance, handle complex escalations, and provide hands-on technical assistance</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">👥</div>
                            <div><strong>Human Support Guides:</strong> 5 (Crowd Control/Wayfinding) - Focus on physical presence and general participant assistance</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🏥</div>
                            <div><strong>Medical/Safety:</strong> 8 (EMTs, first aid) for immediate response and zero incidents</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">📦</div>
                            <div><strong>Logistics Coordinators:</strong> 10 (setup, breakdown, supplies) for smooth operational flow</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">👔</div>
                            <div><strong>Supervisors:</strong> 7 (1:7-10 span of control) enabling rapid decision-making</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🎯</div>
                            <div><strong>Hippocratic AI Agents</strong> (Scalable On-Demand Support): Provide automated registration, technical troubleshooting via app/kiosk, virtual round monitoring, and real-time FAQ answers</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SLIDE 4: Proactive Risk Management -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">04</div>
                <div class="slide-title">Proactive Risk Management</div>
            </div>
            <div class="slide-content">
                <div class="content-grid">
                    <div class="risk-matrix-wrapper">
                        <h3 style="text-align: center; margin-bottom: 10px; color: #1E293B;">Risk Priority Matrix</h3>
                        <div style="font-size: 12px; text-align: center; color: #64748B; margin-bottom: 10px;">High Impact → | ↑ High Probability</div>
                        
                        <div class="risk-matrix">
                            <div class="risk-cell risk-high-high">
                                Weather<br>Disruption
                            </div>
                            <div class="risk-cell risk-low-high">
                                Technology<br>Failure
                            </div>
                            <div class="risk-cell risk-high-low">
                                Participant<br>Confusion
                            </div>
                            <div class="risk-cell risk-low-low">
                                Volunteer<br>Shortage
                            </div>
                        </div>
                    </div>
                    
                    <div class="mitigation-strategies">
                        <div class="mitigation-title">Comprehensive Mitigation Strategies</div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Redundant Tournament Tech</div>
                            <div class="mitigation-action">Utilize offline paper brackets, mobile hotspots, and pre-configured emergency laptops as comprehensive backups</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Equipment (100% Backup Strategy)</div>
                            <div class="mitigation-action">20 primary high-durability tic-tac-toe sets for active courts, plus 20 additional sets (100% backup) staged for immediate replacement. All court materials are weather-resistant (marine-grade plywood, weatherproof paint)</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Medical Emergencies (Rapid Response Protocol)</div>
                            <div class="mitigation-action">Dedicated on-site EMT team with a fully stocked first-aid station. Pre-established direct communication channels and transport agreements with Stanford Health Care for immediate hospital coordination</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Crowd Management (Dynamic Flow Control)</div>
                            <div class="mitigation-action">Implement clear signage, designated entry/exit points, and staffed flow control barriers</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Vendor Issues (Dual Sourcing Strategy)</div>
                            <div class="mitigation-action">For all critical services (e.g., catering, security), establish contracts with at least two pre-qualified backup suppliers</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Communication Protocols (Real-Time Transparency)</div>
                            <div class="mitigation-action">Multi-Channel Real-Time Updates: Deliver critical updates (weather, schedule changes, match status) via SMS, dedicated event mobile app push notifications, and email to ensure redundancy and reach. AI agents proactively deliver personalized alerts and answer follow-up questions</div>
                        </div>
                        
                        <div class="mitigation-item">
                            <div class="mitigation-risk">Volunteer Incident Reporting Network</div>
                            <div class="mitigation-action">Equip all key volunteers with two-way radios connected to a central command center, enabling immediate incident reporting and rapid escalation to designated supervisors for resolution</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SLIDE 5: Change Management Strategies -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">05</div>
                <div class="slide-title">Change Management Strategies</div>
            </div>
            <div class="slide-content">
                <div class="change-story">
                    <div class="story-card">
                        <div class="story-icon">👥</div>
                        <div class="story-title">Participant Journey</div>
                        <div class="story-content">
                            5 tailored personas (Competitive Pro, Casual Gamer, Family, Accessibility) with personalized communication strategies. 
                            100-person champion network serves as event ambassadors, creating peer-to-peer advocacy and reducing resistance.
                        </div>
                    </div>
                    
                    <div class="story-card">
                        <div class="story-icon">🤝</div>
                        <div class="story-title">Sponsor Alignment</div>
                        <div class="story-content">
                            Co-creation workshops link tournament goals to sponsor objectives. Real-time ROI dashboard tracks brand impressions, 
                            positioning partners as technology collaboration leaders while ensuring measurable value delivery.
                        </div>
                    </div>
                    
                    <div class="story-card">
                        <div class="story-icon">🛡️</div>
                        <div class="story-title">Resistance Mitigation</div>
                        <div class="story-content">
                            Pre-mapped friction points (rules complexity, parking, fairness) with scripted AI agent responses. 
                            30-minute escalation protocol for negative feedback with human intervention and rapid resolution.
                        </div>
                    </div>
                </div>
                
                <div class="content-grid">
                    <div class="content-section">
                        <div class="section-title">Engagement Framework</div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🎯</div>
                            <div><strong>Behavioral Nudges:</strong> Gamification, achievement badges, live leaderboards</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🗺️</div>
                            <div><strong>Journey Mapping:</strong> Registration → Virtual play → Live event → Advocacy</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">📱</div>
                            <div><strong>Multi-Channel Communication:</strong> SMS, app notifications, email updates</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🏆</div>
                            <div><strong>Recognition Programs:</strong> Early adopter badges, champion status, social sharing</div>
                        </div>
                    </div>
                    
                    <div class="content-section">
                        <div class="section-title">Continuous Monitoring</div>
                        <div class="bullet-point">
                            <div class="bullet-icon">📊</div>
                            <div><strong>Real-Time Feedback:</strong> In-app surveys, QR code feedback, AI interaction logs</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🚨</div>
                            <div><strong>Early Warning System:</strong> Predictive identification of engagement issues</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">🔄</div>
                            <div><strong>Iterative Optimization:</strong> Live adjustments based on participant feedback</div>
                        </div>
                        <div class="bullet-point">
                            <div class="bullet-icon">📈</div>
                            <div><strong>Sentiment Tracking:</strong> Automated analysis of participant communications</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- SLIDE 6: Strategic Implementation Timeline -->
        <div class="slide">
            <div class="slide-header">
                <div class="slide-number">06</div>
                <div class="slide-title">Strategic Implementation Timeline</div>
            </div>
            <div class="slide-content">
                <div class="gantt-container">
                    <div class="gantt-header">
                        <div></div>
                        <div class="gantt-week">W1</div>
                        <div class="gantt-week">W2</div>
                        <div class="gantt-week">W3</div>
                        <div class="gantt-week">W4</div>
                        <div class="gantt-week">W5</div>
                        <div class="gantt-week">W6</div>
                        <div class="gantt-week">W7</div>
                        <div class="gantt-week">W8</div>
                        <div class="gantt-week">W9</div>
                        <div class="gantt-week">W10</div>
                        <div class="gantt-week">W11</div>
                        <div class="gantt-week">W12</div>
                        <div class="gantt-week">W13</div>
                        <div class="gantt-week">W14</div>
                        <div class="gantt-week">W15</div>
                        <div class="gantt-week">W16</div>
                        <div class="gantt-week">W17</div>
                        <div class="gantt-week">W18</div>
                        <div class="gantt-week">W19</div>
                        <div class="gantt-week">W20</div>
                        <div class="gantt-week">W21</div>
                        <div class="gantt-week">W22</div>
                        <div class="gantt-week">W23</div>
                        <div class="gantt-week">W24</div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Discovery & Stakeholder Alignment</div>
                        <div class="gantt-bar phase-discovery" style="grid-column: span 8;">AI interviews • Needs analysis • Advisory board</div>
                        <div style="grid-column: span 16;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Vendor Selection & Sponsorship</div>
                        <div class="gantt-bar phase-discovery" style="grid-column: span 8;">Partnership development • Contract negotiations</div>
                        <div style="grid-column: span 16;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Platform Design & Development</div>
                        <div style="grid-column: span 6;"></div>
                        <div class="gantt-bar phase-design" style="grid-column: span 8;">Tech stack • UX design • Integration testing</div>
                        <div style="grid-column: span 10;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Critical Pilot Testing</div>
                        <div style="grid-column: span 12;"></div>
                        <div class="gantt-bar phase-pilot" style="grid-column: span 4;">100-person validation • A/B optimization</div>
                        <div style="grid-column: span 8;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Virtual Tournament Rounds</div>
                        <div style="grid-column: span 16;"></div>
                        <div class="gantt-bar phase-prep" style="grid-column: span 4;">1000 → 200 qualification</div>
                        <div style="grid-column: span 4;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Live Event Execution</div>
                        <div style="grid-column: span 20;"></div>
                        <div class="gantt-bar phase-event" style="grid-column: span 2;">Event Day</div>
                        <div style="grid-column: span 2;"></div>
                    </div>
                    
                    <div class="gantt-row">
                        <div class="gantt-task">Post-Event Analysis & Documentation</div>
                        <div style="grid-column: span 22;"></div>
                        <div class="gantt-bar phase-analysis" style="grid-column: span 2;">ROI • Feedback • Playbook</div>
                    </div>
                </div>
                
                <div class="highlight-box">
                    <div class="highlight-title">🎯 Critical Success Factors</div>
                    <div style="font-size: 16px; margin-top: 15px;">
                        <strong>Pilot Testing</strong> enables optimization before virtual rounds, reducing execution risk. 
                        <strong>Post-event analysis</strong> captures ROI metrics, participant feedback, and operational insights for replicable framework 
                        development with proven scalability.
                    </div>
                </div>
            </div>
        </div>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            console.log('Tournament presentation loaded successfully - Version 2');
        });
    </script>
</body>
</html>
