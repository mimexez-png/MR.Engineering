<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MR ENGINEERING - ผู้เชี่ยวชาญด้านวิศวกรรม</title>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #0f172a; 
            --primary-light: #1e293b;
            --secondary: #ff6b35; 
            --dark: #060913;
            --text: #f8fafc;
            --text-gray: #94a3b8;
            --success: #10b981;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Sarabun', sans-serif; scroll-behavior: smooth; }
        body { background-color: var(--dark); color: var(--text); overflow-x: hidden; }

        header {
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0; left: 0; z-index: 100;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .logo { font-size: 24px; font-weight: 700; color: #fff; letter-spacing: 1px; }
        .logo span { color: var(--secondary); }
        
        .nav-links { display: flex; gap: 25px; list-style: none; }
        .nav-links a { color: var(--text); text-decoration: none; font-weight: 500; transition: color 0.3s; }
        .nav-links a:hover { color: var(--secondary); }

        .login-trigger-btn {
            background: transparent; border: 1px solid var(--secondary); color: var(--secondary);
            padding: 8px 18px; border-radius: 5px; cursor: pointer; font-weight: 600; transition: all 0.3s;
        }
        .login-trigger-btn:hover { background: var(--secondary); color: white; }

        section { padding: 80px 5%; max-width: 1200px; margin: 0 auto; }
        .section-title { font-size: 32px; font-weight: 700; text-align: center; margin-bottom: 40px; position: relative; }
        .section-title::after { content: ''; width: 60px; height: 4px; background: var(--secondary); display: block; margin: 10px auto 0; border-radius: 2px; }

        .hero-section { 
            padding-top: 160px; padding-bottom: 100px; text-align: center; 
            background: radial-gradient(circle at center, var(--primary-light) 0%, var(--dark) 100%);
            max-width: 100%;
        }
        .hero-content { max-width: 800px; margin: 0 auto; }
        .hero-title { font-size: 48px; margin-bottom: 20px; font-weight: 700; line-height: 1.2; }
        .hero-desc { color: var(--text-gray); font-size: 18px; line-height: 1.6; white-space: pre-line; margin-bottom: 30px; }

        .services-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .service-card { 
            background: var(--primary-light); padding: 40px 30px; border-radius: 12px; 
            text-align: center; border: 1px solid rgba(255,255,255,0.05); transition: transform 0.3s;
        }
        .service-card:hover { transform: translateY(-10px); border-color: var(--secondary); }
        .service-icon { font-size: 40px; color: var(--secondary); margin-bottom: 20px; }
        .service-card h3 { font-size: 20px; margin-bottom: 15px; }
        .service-card p { color: var(--text-gray); font-size: 15px; line-height: 1.6; }

        .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 20px; }
        .gallery-item { 
            position: relative; background: var(--primary); border-radius: 10px; overflow: hidden; 
            aspect-ratio: 4/3; border: 1px solid rgba(255,255,255,0.1);
        }
        .gallery-item img, .gallery-item video { width: 100%; height: 100%; object-fit: cover; transition: transform 0.3s; }
        .gallery-item:hover img { transform: scale(1.05); }

        .contact-section { background: var(--primary-light); max-width: 100%; padding-bottom: 60px; }
        .contact-container { max-width: 800px; margin: 0 auto; display: flex; flex-direction: column; gap: 30px; }
        .contact-box { 
            display: flex; align-items: center; gap: 20px; background: rgba(0,0,0,0.2); 
            padding: 25px; border-radius: 12px; border-left: 4px solid var(--secondary);
            transition: all 0.3s ease;
        }
        .contact-box:hover { background: rgba(0,0,0,0.4); border-color: var(--success); }
        .contact-icon { width: 60px; height: 60px; background: rgba(255,107,53,0.1); color: var(--secondary); border-radius: 50%; display: flex; justify-content: center; align-items: center; font-size: 24px; flex-shrink: 0; }
        .contact-info h4 { font-size: 18px; margin-bottom: 5px; color: #fff; }
        .contact-info p, .contact-info a { color: var(--text-gray); font-size: 16px; line-height: 1.5; white-space: pre-line; text-decoration: none; transition: color 0.3s; }
        .contact-info a:hover { color: var(--secondary); text-decoration: underline; }

        footer { text-align: center; padding: 20px; background: #000; color: var(--text-gray); font-size: 14px; border-top: 1px solid rgba(255,255,255,0.05); }
        footer a { color: var(--text-gray); text-decoration: none; transition: color 0.3s; }
        footer a:hover { color: var(--secondary); }

        /* ================= 3. เครื่องมือแอดมิน ================= */
        .admin-only { display: none !important; } 
        
        .admin-top-bar {
            background: #ff6b35; color: white; padding: 10px; text-align: center; font-weight: 600;
            position: fixed; top: 0; left: 0; width: 100%; z-index: 1001; display: flex; justify-content: center; align-items: center; gap: 20px;
        }
        .logout-btn { background: #000; color: #fff; border: none; padding: 4px 12px; border-radius: 5px; cursor: pointer; font-size: 13px; }

        .edit-btn {
            background: #3b82f6; color: white; border: none; padding: 8px 16px; border-radius: 5px;
            margin-top: 15px; cursor: pointer; font-size: 14px; display: inline-flex; align-items: center; gap: 5px; transition: background 0.3s;
        }
        .edit-btn:hover { background: #2563eb; }

        .delete-media-btn {
            position: absolute; top: 10px; right: 10px; background: rgba(220,53,69,0.9); border: none;
            color: white; width: 32px; height: 32px; border-radius: 50%; cursor: pointer; font-size: 16px; z-index: 10;
        }

        .add-media-card {
            border: 2px dashed rgba(255,255,255,0.2); display: flex; flex-direction: column;
            justify-content: center; align-items: center; cursor: pointer; transition: all 0.3s; gap: 10px; color: var(--text-gray); background: transparent;
        }
        .add-media-card:hover { border-color: var(--secondary); color: #fff; background: rgba(255,107,53,0.05); }

        .super-key-box {
            position: fixed; bottom: 20px; left: 20px; background: var(--primary-light); border: 1px solid #00d9ff;
            padding: 15px; border-radius: 12px; z-index: 99; max-width: 280px; box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        }

        /* ================= 4. หน้าต่างล็อกอิน ================= */
        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); backdrop-filter: blur(5px);
            display: flex; justify-content: center; align-items: center; z-index: 2000; visibility: hidden; opacity: 0; transition: all 0.3s;
        }
        .modal-overlay.active { visibility: visible; opacity: 1; }
        .modal-box { background: var(--primary-light); padding: 40px 30px; border-radius: 15px; width: 100%; max-width: 400px; position: relative; box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5); }
        .close-modal { position: absolute; top: 15px; right: 15px; background: transparent; border: none; color: var(--text-gray); font-size: 24px; cursor: pointer; }
        
        .form-group { margin-bottom: 20px; position: relative; }
        .form-group i { position: absolute; left: 15px; top: 50%; transform: translateY(-50%); color: var(--text-gray); }
        .form-group input {
            width: 100%; padding: 14px 15px 14px 45px; background: rgba(0,0,0,0.2); border: 1px solid rgba(255,255,255,0.1); border-radius: 8px; color: white; font-size: 15px;
        }
        .form-group input:focus { outline: none; border-color: var(--secondary); }
        .btn-submit { width: 100%; padding: 14px; background: linear-gradient(to right, var(--secondary), #ea580c); border: none; border-radius: 8px; color: white; font-weight: 600; cursor: pointer; font-size: 16px; }
        .switch-link { text-align: center; margin-top: 20px; font-size: 14px; color: var(--text-gray); }
        .switch-link a { color: var(--secondary); cursor: pointer; text-decoration: none; font-weight: 600; }
        .hidden { display: none; }
    </style>
</head>
<body>

    <div id="admin-top-bar" class="admin-top-bar admin-only">
        <span id="admin-status-text"><i class="fas fa-tools"></i> เข้าสู่โหมดจัดการเว็บไซต์</span>
        <button class="logout-btn" onclick="logoutAdmin()"><i class="fas fa-sign-out-alt"></i> ออกจากระบบ</button>
    </div>

    <header id="main-header">
        <div class="logo">MR <span>ENGINEERING</span></div>
        <ul class="nav-links">
            <li><a href="#home">หน้าแรก</a></li>
            <li><a href="#services">บริการของเรา</a></li>
            <li><a href="#portfolio">ผลงาน</a></li>
            <li><a href="#contact">ติดต่อเรา</a></li>
        </ul>
        <button class="login-trigger-btn" id="login-nav-btn" onclick="openLoginModal()"><i class="fas fa-lock"></i> ผู้ดูแลระบบ</button>
    </header>

    <section id="home" class="hero-section">
        <div class="hero-content">
            <h1 class="hero-title" id="web-title">ผู้เชี่ยวชาญด้านระบบวิศวกรรม<br>ครบวงจรระดับมืออาชีพ</h1>
            <p class="hero-desc" id="web-desc">รับออกแบบ ติดตั้ง และให้คำปรึกษาด้านวิศวกรรมด้วยมาตรฐานสูงสุด โดยทีมงานวิศวกรที่มีประสบการณ์ เพื่อตอบสนองทุกความต้องการของธุรกิจคุณ</p>
            <button class="edit-btn admin-only" onclick="editWebsiteText()"><i class="fas fa-edit"></i> แก้ไขหัวข้อ & รายละเอียด</button>
        </div>
    </section>

    <section id="services">
        <h2 class="section-title">บริการของเรา</h2>
        <div class="services-grid">
            <div class="service-card">
                <i class="fas fa-drafting-compass service-icon"></i>
                <h3>ออกแบบระบบวิศวกรรม</h3>
                <p>บริการออกแบบระบบต่างๆ ภายในอาคารและโรงงานอุตสาหกรรม ให้ถูกต้องตามหลักวิศวกรรมและประหยัดพลังงาน</p>
            </div>
            <div class="service-card">
                <i class="fas fa-tools service-icon"></i>
                <h3>รับเหมาติดตั้ง</h3>
                <p>ดำเนินการติดตั้งระบบโดยทีมช่างผู้ชำนาญการ พร้อมควบคุมงานอย่างใกล้ชิดเพื่อให้ได้งานที่มีคุณภาพและปลอดภัย</p>
            </div>
            <div class="service-card">
                <i class="fas fa-user-tie service-icon"></i>
                <h3>ให้คำปรึกษาและซ่อมบำรุง</h3>
                <p>ดูแลระบบอย่างต่อเนื่อง พร้อมให้คำปรึกษาและแก้ไขปัญหาทางวิศวกรรมเพื่อให้ระบบทำงานได้อย่างเต็มประสิทธิภาพ</p>
            </div>
        </div>
    </section>

    <section id="portfolio">
        <h2 class="section-title">ผลงานของเรา</h2>
        <div class="gallery-grid" id="main-gallery-grid">
            </div>
    </section>

    <section id="contact" class="contact-section">
        <br><br>
        <h2 class="section-title">ติดต่อเรา</h2>
        <div class="contact-container">
            <div class="contact-box">
                <div class="contact-icon"><i class="fas fa-map-marker-alt"></i></div>
                <div class="contact-info">
                    <h4>ที่อยู่สำนักงาน (แผนที่)</h4>
                    <p id="web-address">
                        <a href="https://maps.google.com/?cid=6076344801984346852&g_mp=Cidnb29nbGUubWFwcy5wbGFjZXMudjEuUGxhY2VzLlNlYXJjaFRleHQ" target="_blank" title="เปิดดูบน Google Maps">
                            ศุภณัฐวัสดุก่อสร้าง<br>ตำบลหินซ้อน อำเภอแก่งคอย จังหวัดสระบุรี
                        </a>
                    </p>
                </div>
            </div>
            <div class="contact-box">
                <div class="contact-icon"><i class="fas fa-phone-alt"></i></div>
                <div class="contact-info">
                    <h4>เบอร์โทรศัพท์ติดต่อ (สายด่วน)</h4>
                    <p id="web-phone">
                        <a href="tel:0819947715">081-994-7715</a> , 
                        <a href="tel:0898304774">089-830-4774</a>
                    </p>
                </div>
            </div>
            
            <div style="text-align: center;">
                <button class="edit-btn admin-only" onclick="alert('เนื่องจากฝังลิงก์พิเศษให้ลูกค้ากดแผนที่และโทรออก หากต้องการแก้ไขลิงก์สามารถปรับเปลี่ยนที่โค้ดส่วน contact-box ได้โดยตรงครับ')"><i class="fas fa-info-circle"></i> การแก้ไขที่อยู่และเบอร์โทร</button>
            </div>
        </div>
    </section>

    <footer>
        <p>
            <a href="https://maps.google.com/?cid=6076344801984346852&g_mp=Cidnb29nbGUubWFwcy5wbGFjZXMudjEuUGxhY2VzLlNlYXJjaFRleHQ" target="_blank"><i class="fas fa-map-marker-alt" style="color: var(--secondary); margin-right:5px;"></i> ศุภณัฐวัสดุก่อสร้าง ตำบลหินซ้อน อำเภอแก่งคอย จังหวัดสระบุรี</a>
            <br><br>&copy; 2026 MR ENGINEERING. All rights reserved.
        </p>
    </footer>

    <div id="super-key-box" class="super-key-box admin-only">
        <span style="color: #00d9ff; font-weight: 600; font-size: 14px;"><i class="fas fa-key"></i> สร้าง Key ให้แอดมินร่วม</span>
        <button onclick="generateNewKey()" style="background:#00d9ff; color:#000; border:none; padding:8px 10px; font-weight:bold; width:100%; border-radius:5px; margin-top:10px; cursor:pointer;">+ กดเพื่อสร้าง Key ใหม่</button>
        <div id="key-display" style="margin-top:10px; font-size:14px; color:#fff; text-align:center; font-family:monospace; background:#000; padding:5px; border-radius:4px;"></div>
    </div>

    <input type="file" id="hidden-file-input" accept="image/*,video/*" multiple class="hidden" onchange="processNewMedia(this)">

    <div class="modal-overlay" id="login-modal">
        <div class="modal-box">
            <button class="close-modal" onclick="closeLoginModal()">×</button>
            
            <div id="login-form-panel">
                <h3 style="text-align:center; margin-bottom:25px; font-size:22px;">เข้าสู่ระบบผู้ดูแล</h3>
                <div class="form-group">
                    <i class="fas fa-envelope"></i>
                    <input type="email" id="login-email" placeholder="อีเมล" required>
                </div>
                <div class="form-group">
                    <i class="fas fa-lock"></i>
                    <input type="password" id="login-password" placeholder="รหัสผ่าน" required>
                </div>
                <button class="btn-submit" onclick="submitLogin()">เข้าสู่ระบบ</button>
                <div class="switch-link">แอดมินคนใหม่? <a onclick="switchPanel('register')">ลงทะเบียนขอสิทธิ์</a></div>
            </div>

            <div id="register-form-panel" class="hidden">
                <h3 style="text-align:center; margin-bottom:25px; font-size:22px; color:var(--success);">ลงทะเบียนแอดมิน</h3>
                <div class="form-group">
                    <i class="fas fa-envelope"></i>
                    <input type="email" id="reg-email" placeholder="อีเมลของคุณ" required>
                </div>
                <div class="form-group">
                    <i class="fas fa-lock"></i>
                    <input type="password" id="reg-password" placeholder="ตั้งรหัสผ่าน" required>
                </div>
                <div class="form-group">
                    <i class="fas fa-key"></i>
                    <input type="text" id="reg-key" placeholder="กรอก Key ยืนยันสิทธิ์" required>
                </div>
                <button class="btn-submit" style="background:var(--success);" onclick="submitRegister()">ยืนยันลงทะเบียน</button>
                <div class="switch-link">มีบัญชีแล้ว? <a onclick="switchPanel('login')">กลับไปล็อกอิน</a></div>
            </div>
        </div>
    </div>

    <script>
        const MAIN_ADMIN = { email: "mimexez@gmail.com", password: "topmimex1234" };
        let dbCoAdmins = []; 
        let dbValidKeys = ["MR-1111", "MR-2222"];
        let currentRole = "guest";
        
        let initialMedia = [
            { type: 'image', src: '67357.jpg' },
            { type: 'image', src: '67355.jpg' },
            { type: 'image', src: '67356.jpg' },
            { type: 'image', src: '67352.jpg' },
            { type: 'image', src: '67353.jpg' },
            { type: 'image', src: '67354.jpg' },
            { type: 'image', src: '67350.jpg' },
            { type: 'image', src: '67351.jpg' }
        ];

        window.onload = () => { renderGallery(); };

        function openLoginModal() { document.getElementById('login-modal').classList.add('active'); }
        function closeLoginModal() { document.getElementById('login-modal').classList.remove('active'); }
        function switchPanel(panel) {
            if(panel === 'register') {
                document.getElementById('login-form-panel').classList.add('hidden');
                document.getElementById('register-form-panel').classList.remove('hidden');
            } else {
                document.getElementById('register-form-panel').classList.add('hidden');
                document.getElementById('login-form-panel').classList.remove('hidden');
            }
        }

        function submitLogin() {
            const email = document.getElementById('login-email').value.trim();
            const pass = document.getElementById('login-password').value;
            if(!email || !pass) { alert("กรุณากรอกข้อมูลให้ครบถ้วน"); return; }

            if(email === MAIN_ADMIN.email && pass === MAIN_ADMIN.password) {
                activateAdminMode("super-admin", email);
            } else {
                const coAdmin = dbCoAdmins.find(u => u.email === email && u.password === pass);
                if(coAdmin) {
                    activateAdminMode("co-admin", email);
                } else {
                    alert("อีเมลหรือรหัสผ่านไม่ถูกต้อง");
                }
            }
        }

        function submitRegister() {
            const email = document.getElementById('reg-email').value.trim();
            const pass = document.getElementById('reg-password').value;
            const key = document.getElementById('reg-key').value.trim();

            if(!email || !pass || !key) { alert("กรุณากรอกข้อมูลให้ครบ"); return; }
            if(email === MAIN_ADMIN.email) { alert("อีเมลนี้เป็นของแอดมินหลักอยู่แล้ว"); return; }
            if(dbCoAdmins.some(u => u.email === email)) { alert("อีเมลนี้ถูกลงทะเบียนไปแล้ว"); return; }

            const keyIndex = dbValidKeys.indexOf(key);
            if(keyIndex !== -1) {
                dbCoAdmins.push({ email: email, password: pass });
                dbValidKeys.splice(keyIndex, 1);
                alert("ลงทะเบียนสำเร็จ! กรุณาล็อกอิน");
                switchPanel('login');
            } else {
                alert("Key ไม่ถูกต้อง หรือถูกใช้งานไปแล้ว");
            }
        }

        function activateAdminMode(role, email) {
            currentRole = role;
            closeLoginModal();
            document.getElementById('login-nav-btn').classList.add('hidden');
            document.getElementById('main-header').style.top = "40px";

            document.querySelectorAll('.admin-only').forEach(el => el.style.display = 'inline-flex');

            if(role === 'super-admin') {
                document.getElementById('admin-status-text').innerHTML = `<i class="fas fa-crown"></i> แอดมินหลัก (${email})`;
                document.getElementById('super-key-box').style.display = 'block';
            } else {
                document.getElementById('admin-status-text').innerHTML = `<i class="fas fa-user-cog"></i> แอดมินร่วม (${email})`;
                document.getElementById('super-key-box').style.setProperty('display', 'none', 'important');
            }
            renderGallery();
        }

        function logoutAdmin() {
            currentRole = "guest";
            document.getElementById('login-nav-btn').classList.remove('hidden');
            document.getElementById('main-header').style.top = "0";
            
            document.querySelectorAll('.admin-only').forEach(el => el.style.setProperty('display', 'none', 'important'));
            
            document.getElementById('login-email').value = "";
            document.getElementById('login-password').value = "";
            renderGallery();
        }

        function generateNewKey() {
            const newKey = "MR-" + Math.floor(1000 + Math.random() * 9000);
            dbValidKeys.push(newKey);
            document.getElementById('key-display').innerText = newKey;
        }

        function editWebsiteText() {
            const currentTitle = document.getElementById('web-title').innerHTML.replace(/<br>/g, '\n');
            const currentDesc = document.getElementById('web-desc').innerText;

            const newTitle = prompt("แก้ไขหัวข้อหลัก (พิมพ์ \\n เพื่อขึ้นบรรทัดใหม่):", currentTitle);
            if (newTitle !== null && newTitle.trim() !== "") {
                document.getElementById('web-title').innerHTML = newTitle.replace(/\\n|\n/g, '<br>');
            }

            const newDesc = prompt("แก้ไขรายละเอียดบริษัท:", currentDesc);
            if (newDesc !== null && newDesc.trim() !== "") {
                document.getElementById('web-desc').innerText = newDesc;
            }
        }

        function renderGallery() {
            const grid = document.getElementById('main-gallery-grid');
            grid.innerHTML = "";

            initialMedia.forEach((media, index) => {
                const item = document.createElement('div');
                item.className = "gallery-item";
                
                if(media.type === 'image') {
                    item.innerHTML = `<img src="${media.src}" alt="ผลงานวิศวกรรม">`;
                } else {
                    item.innerHTML = `<video src="${media.src}" controls></video>`;
                }

                if(currentRole !== 'guest') {
                    const delBtn = document.createElement('button');
                    delBtn.className = "delete-media-btn";
                    delBtn.innerHTML = '<i class="fas fa-trash-alt"></i>';
                    delBtn.onclick = function() {
                        if(confirm('ต้องการลบผลงานนี้ใช่หรือไม่?')) {
                            initialMedia.splice(index, 1);
                            renderGallery();
                        }
                    };
                    item.appendChild(delBtn);
                }
                grid.appendChild(item);
            });

            if(currentRole !== 'guest') {
                const addCard = document.createElement('div');
                addCard.className = "gallery-item add-media-card";
                addCard.innerHTML = `<i class="fas fa-cloud-upload-alt" style="font-size:36px;"></i><span>เพิ่มผลงานใหม่</span>`;
                addCard.onclick = () => document.getElementById('hidden-file-input').click();
                grid.appendChild(addCard);
            }
        }

        function processNewMedia(input) {
            const files = input.files;
            for(let i=0; i<files.length; i++) {
                const file = files[i];
                const fileUrl = URL.createObjectURL(file);
                const fileType = file.type.startsWith('video/') ? 'video' : 'image';
                initialMedia.push({ type: fileType, src: fileUrl });
            }
            renderGallery();
            input.value = ""; 
        }
    </script>
</body>
</html>
