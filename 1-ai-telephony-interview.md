# 🏗️ AI Telephony Architecture Evolution Interview Script

**Duration:** 30-45 menit  
**Format:** Story-driven Design Evolution  
**Tool:** Excalidraw for visual architecture  
**Target:** Full Stack Developer (Mid-Senior Level)

---

## 🎬 OPENING WITH INTERVIEW FORMAT (8 menit)

### What You Say:
"Halo! Sebelum kita mulai, gue mau jelasin format interview hari ini sedikit berbeda dari biasanya."

"Instead of traditional Q&A, kita bakal pakai storytelling approach. Jadi gue bakal ceritain scenario development project, terus lo sebagai developer harus design dan evolve architecture berdasarkan challenges yang muncul."

"Think of it kayak pair programming session, tapi focus ke system design. Lo bakal gambar architecture di Excalidraw, terus setiap ada problem baru, lo adjust design lo. Sounds good?"

**[Wait for confirmation, then continue]**

"Perfect! Oke, cerita kita mulai."

"Company kita lagi develop AI telephony system. Basically, product yang bikin user bisa telepon dan ngomong langsung sama AI - kayak customer service tapi fully automated."

"Background nya, CEO kita frustrated sama customer service experience di mana-mana. Dia mikir 'kenapa gue ga bisa langsung telepon dan ngomong sama AI yang smart, instead of nunggu 30 menit di queue atau navigate menu yang annoying?'"

"Sekarang kita udah dapat green light buat develop MVP. Product vision nya simple tapi challenging:"
- "User bisa telepon ke nomor yang kita sediain"
- "Langsung connect ke AI yang bisa ngomong natural"
- "AI bisa jawab pertanyaan, kasih informasi, bahkan handle simple tasks"
- "Conversation harus smooth kayak ngomong sama manusia"

"Target market awal: small businesses yang butuh customer service automation. Misal restaurant buat reservation, clinic buat appointment booking, atau service company buat basic inquiry."

"Lo sebagai full stack developer di team ini, diminta design initial architecture buat MVP. Requirements teknis nya:"
- "Handle simultaneous calls, mulai dari 50-100 concurrent"
- "Support bahasa Indonesia"
- "Response time di bawah 3 detik"
- "Basic conversation memory, jadi AI inget context"

"Bisa gambar di Excalidraw gimana architecture nya dari user call sampai AI response? Think through the whole journey step by step."

### Let Them Think and Draw (5-6 menit)

### Guide if Needed:
"Take your time. Pikirin step by step - user dial nomor, terus apa yang terjadi di backend kita?"

### What You're Looking For:
✅ **Good Initial Design:**
- Clear call flow: Phone → Gateway → STT → AI → TTS → Phone
- Session management component
- Database untuk conversation state
- API orchestration layer
- Basic error handling

❌ **Weak Initial Design:**
- Terlalu simple linear flow
- Missing key components
- Ga ada session/state management
- Unclear data processing

### Quick Review:
"Nice initial architecture! Sekarang gue mau test design lo dengan real challenges yang bakal muncul pas development dan production. Setiap challenge mungkin butuh lo adjust design nya. Ready?"

---

## 🚨 CHALLENGE 1: Demo Day Disaster (7 menit)

### What You Say:
"Fast forward 2 bulan development, MVP udah jadi. Demo day ke potential investors!"

"Demo preparation: 5 concurrent call buat showcase. Everything works perfect pas practice runs."

"Demo day arrive: 20 investor interested, mereka semua mau coba langsung. Tiba-tiba everyone calling simultaneously buat test system."

"Hasilnya: disaster!"
- "Call timeout setelah 30 detik"
- "STT service return error"
- "AI response butuh 10+ detik"
- "Beberapa call completely dropped"
- "System memory spike ke 100%"

"Investor mulai pergi, CEO panic. Lo punya 2 jam buat fix sebelum follow-up demo session."

"Gimana lo quickly evolve architecture buat handle unexpected concurrent load? Update design lo!"

### Watch Them Redesign (4-5 menit)

### What You're Looking For:
✅ **Good Scaling Evolution:**
- Load balancer tambahan
- Queue system
- Resource pooling
- Connection management
- Basic caching

❌ **Poor Scaling Response:**
- Ga ada systematic approach
- Cuma bilang "tambahin server"
- Missing bottleneck analysis
- Ga ada queue management

### Follow-up:
"Good crisis thinking! Dari semua changes yang lo buat, mana yang paling critical buat immediate fix?"

---

## 💰 CHALLENGE 2: The Cost Reality (7 menit)

### What You Say:
"Demo saved! Investor impressed, dapet funding round. Team celebrate!"

"1 bulan kemudian, CTO datang: 'Bro, monthly bill udah 5000 dollar padahal baru 1000 test call. Kalo scale ke 10,000 call per bulan, itu 50,000 dollar operational cost!'"

"Breakdown cost:"
- "STT API: 2000 dollar"
- "TTS API: 1500 dollar"
- "AI processing: 1000 dollar"
- "Infrastructure: 500 dollar"

"Analysis nunjukin:"
- "STT running terus menerus, bahkan pas user ga ngomong"
- "TTS generate audio baru buat response yang sama berulang kali"
- "AI process pertanyaan serupa dari awal tiap kali"
- "Conversation panjang consume resource terus tanpa cleanup"

"CTO bilang: 'Kita harus cut cost ini 80% atau product ga viable. Bisa optimize ga?'"

"Gimana lo redesign buat dramatically reduce operational cost?"

### Watch Them Optimize (4-5 menit)

### What You're Looking For:
✅ **Good Cost Evolution:**
- Smart caching system
- Session lifecycle management
- Response templating
- STT triggering yang intelligent (silence detection)
- Resource cleanup automation

❌ **Poor Cost Response:**
- Ga ada optimization strategy yang spesifik
- Generic "cari API yang lebih murah"
- Missing caching opportunity
- Ga ada lifecycle management

### Follow-up:
"Smart optimization! Potential trade-off dari caching strategy lo apa buat user experience?"

---

## 🎤 CHALLENGE 3: Real User Feedback (7 menit)

### What You Say:
"Cost optimized! Monthly operational turun ke 1000 dollar buat 10,000 call. Team happy."

"Soft launch ke 50 beta user (small business). Feedback mulai masuk:"

"Restaurant owner: 'AI ga ngerti pas gue ngomong sambil masak, ada background noise kompor sama musik.'"

"Clinic receptionist: 'Patient elderly ngomong pelan banget, AI potong mereka thinking udah selesai ngomong.'"

"Service company: 'Teknisi kita call dari lapangan, network connection unstable, audio choppy.'"

"Beta testing metrics:"
- "Call completion rate: 60% (target: 90%)"
- "User satisfaction: 2.8/5"
- "Average STT accuracy: 65%"

"Product manager stress: 'User bakal churn kalo kita ga bisa handle real-world audio condition. Harus fix sebelum public launch.'"

"Gimana lo enhance architecture buat handle messy real-world audio situation?"

### Watch Them Add Audio Intelligence (4-5 menit)

### What You're Looking For:
✅ **Good Audio Evolution:**
- Audio preprocessing pipeline
- Adaptive silence detection
- Network quality handling
- Multiple STT confidence strategy
- Fallback mechanism

❌ **Poor Audio Response:**
- Ga ada preprocessing thinking
- Single approach solution
- Missing edge case handling
- Ga ada user experience consideration

### Follow-up:
"Nice audio improvement! Gimana lo handle edge case: user di tempat sangat berisik, STT confidence tetap rendah?"

---

## 🏢 CHALLENGE 4: Customer Diversity (8 menit)

### What You Say:
"Audio quality fixed! Call completion rate naik ke 85%, user satisfaction 4.1/5. Ready buat public launch!"

"Launch success! Word of mouth spread, different type customer mulai interested:"

"Customer Type A - E-commerce: 'Kita butuh AI yang fast, energetic, bisa handle order inquiry, track package.'"

"Customer Type B - Healthcare: 'AI harus very professional, slow speech, bisa schedule appointment, handle sensitive information.'"

"Customer Type C - Food Delivery: 'Butuh casual AI, Indonesian slang OK, quick response buat menu question.'"

"Setiap customer mau different AI personality, response speed, dan conversation style."

"Current system: single AI model, single voice, single response pattern buat semua."

"Engineering challenge: gimana support different customer need tanpa maintain separate system?"

"Plus, customer A complain: 'Response time jadi lambat since lo add customer B.' Ternyata healthcare conversation typically 3x lebih lama dan more complex."

"Gimana lo redesign architecture jadi flexible buat handle diverse customer requirement without performance interference?"

### Watch Them Add Flexibility (5-6 menit)

### What You're Looking For:
✅ **Good Flexibility Evolution:**
- Configuration-driven personality setting
- Customer-specific resource allocation
- Queue prioritization system
- Performance isolation strategy

❌ **Poor Flexibility Response:**
- Separate system per customer
- Ga ada resource management
- Missing configuration abstraction
- Ga ada performance consideration

### Follow-up:
"Good flexible design! Gimana lo ensure customer A ga affected pas customer B experience traffic spike?"

---

## 🔍 CHALLENGE 5: The Weekend Bug (5 menit)

### What You Say:
"Multi-customer system running smooth selama 1 bulan. Revenue growing, customer happy."

"Tapi weekend, support team notice weird pattern: 'Every Saturday morning 9-11 AM, AI response jadi completely random dan irrelevant.'"

"Lo investigate:"
- "Saturday morning traffic normal"
- "All system metrics healthy"
- "STT accuracy normal"
- "Tapi AI giving answer kayak: customer tanya 'jam operasional berapa?' AI jawab 'cuaca hari ini cerah'"

"Pattern ini consistent 3 weekend berturut-turut. Customer mulai notice dan complain."

"Setelah deeper investigation, lo discover: office building kita every Saturday morning ada fitness class di gym lantai sebelah. Heavy bass music dan instructor teriak-teriak creating audio interference yang somehow confuse AI context understanding."

"Gimana lo add component ke architecture buat detect dan handle unusual environmental factor yang affect AI performance?"

### Watch Final Evolution (3-4 menit)

### What You're Looking For:
✅ **Good Environmental Handling:**
- Audio quality monitoring
- Context validation
- Anomaly detection
- Environmental factor isolation

❌ **Poor Response:**
- Ga ada systematic detection
- Cuma physical solution
- Missing technical prevention

---

## 🏆 FINAL ARCHITECTURE SHOWCASE (5 menit)

### What You Say:
"Amazing evolution! Lo udah transform simple MVP jadi robust multi-customer platform."

"Final review time:"

1. "Compare final architecture sama initial design lo. Evolution paling significant apa?"

2. "Dari semua challenge ini, mana yang paling unexpected dan kenapa?"

3. "Kalo ada developer baru join team besok, part mana dari architecture yang paling tricky buat dia understand?"

4. "Learning terbesar lo tentang building real-time system?"

### What You're Looking For:
✅ **Strong Full Stack Thinking:**
- Clear evolution articulation
- Understanding real-world complexity
- Practical development insight
- User-centric problem solving
