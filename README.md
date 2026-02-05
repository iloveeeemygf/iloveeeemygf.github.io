<!DOCTYPE html>
<html lang="en">
   <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>vape tracker for madison <3</title>
      <link rel="preconnect" href="https://fonts.googleapis.com">
      <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
      <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
      <style>
         * {
         margin: 0;
         padding: 0;
         box-sizing: border-box;
         text-transform: lowercase;
         }
         :root {
         --pink-50: #fdf2f8;
         --pink-100: #fce7f3;
         --pink-200: #fbcfe8;
         --pink-300: #f9a8d4;
         --pink-400: #f472b6;
         --pink-500: #ec4899;
         --pink-600: #db2777;
         --gray-500: #6b7280;
         --gray-600: #4b5563;
         --gray-700: #374151;
         --white: #ffffff;
         --shadow-soft: 0 4px 20px rgba(236, 72, 153, 0.08);
         --shadow-medium: 0 8px 30px rgba(236, 72, 153, 0.12);
         }
         body {
         font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
         background: linear-gradient(180deg, #ffffff 0%, #fff1f2 50%, #ffe4e6 100%);
         min-height: 100vh;
         display: flex;
         flex-direction: column;
         align-items: center;
         justify-content: center;
         padding: 24px;
         color: var(--gray-700);
         line-height: 1.6;
         }
         .container {
         width: 100%;
         max-width: 400px;
         text-align: center;
         }
         .header {
         margin-bottom: 48px;
         opacity: 0;
         animation: fadeIn 0.8s ease-out forwards;
         }
         .header h1 {
         font-size: 1.5rem;
         font-weight: 500;
         color: var(--gray-600);
         margin-bottom: 8px;
         }
         .header p {
         font-size: 0.875rem;
         color: var(--gray-500);
         font-weight: 300;
         }
         .counter-card {
         background: var(--white);
         border-radius: 32px;
         padding: 48px 32px;
         box-shadow: var(--shadow-soft);
         margin-bottom: 32px;
         opacity: 0;
         transform: translateY(20px);
         animation: slideUp 0.8s ease-out 0.2s forwards;
         transition: box-shadow 0.3s ease;
         }
         .counter-card:hover {
         box-shadow: var(--shadow-medium);
         }
         .day-number {
         font-size: 6rem;
         font-weight: 600;
         background: linear-gradient(135deg, var(--pink-500) 0%, var(--pink-600) 100%);
         -webkit-background-clip: text;
         -webkit-text-fill-color: transparent;
         background-clip: text;
         line-height: 1;
         margin-bottom: 8px;
         display: inline-block;
         }
         .day-label {
         font-size: 1.25rem;
         color: var(--gray-500);
         font-weight: 400;
         margin-bottom: 24px;
         }
         .sub-time {
         font-size: 0.85rem;
         color: var(--gray-500);
         margin-top: -12px;
         }
         .encouragement {
         font-size: 1rem;
         color: var(--pink-600);
         font-weight: 500;
         min-height: 24px;
         opacity: 0;
         animation: fadeIn 0.6s ease-out 0.6s forwards;
         }
         .milestone-badge {
         display: inline-flex;
         align-items: center;
         gap: 6px;
         background: linear-gradient(135deg, var(--pink-100) 0%, var(--pink-200) 100%);
         color: var(--pink-600);
         padding: 8px 16px;
         border-radius: 20px;
         font-size: 0.875rem;
         font-weight: 500;
         margin-top: 16px;
         opacity: 0;
         transform: scale(0.9);
         animation: popIn 0.5s ease-out 0.8s forwards;
         }
         .milestone-badge.hidden {
         display: none;
         }
         .actions {
         display: flex;
         flex-direction: column;
         gap: 12px;
         opacity: 0;
         animation: fadeIn 0.8s ease-out 0.4s forwards;
         }
         .btn {
         width: 100%;
         padding: 16px 24px;
         border: none;
         border-radius: 16px;
         font-size: 1rem;
         font-weight: 500;
         font-family: inherit;
         cursor: pointer;
         transition: all 0.3s ease;
         display: flex;
         align-items: center;
         justify-content: center;
         gap: 8px;
         }
         .btn-primary {
         background: linear-gradient(135deg, var(--pink-500) 0%, var(--pink-600) 100%);
         color: var(--white);
         box-shadow: 0 4px 15px rgba(236, 72, 153, 0.3);
         }
         .btn-primary:hover {
         transform: translateY(-2px);
         box-shadow: 0 6px 20px rgba(236, 72, 153, 0.4);
         }
         .btn-primary:active {
         transform: translateY(0);
         }
         .btn-secondary {
         background: var(--white);
         color: var(--gray-600);
         border: 1px solid var(--pink-200);
         }
         .btn-secondary:hover {
         background: var(--pink-50);
         border-color: var(--pink-300);
         }
         .settings {
         margin-top: 32px;
         padding-top: 24px;
         border-top: 1px solid var(--pink-200);
         opacity: 0;
         animation: fadeIn 0.8s ease-out 0.6s forwards;
         }
         .toggle-row {
         display: flex;
         align-items: center;
         justify-content: center;
         gap: 12px;
         font-size: 0.875rem;
         color: var(--gray-500);
         }
         .toggle {
         position: relative;
         width: 48px;
         height: 26px;
         background: var(--pink-200);
         border-radius: 13px;
         cursor: pointer;
         transition: background 0.3s ease;
         }
         .toggle.active {
         background: var(--pink-500);
         }
         .toggle-knob {
         position: absolute;
         top: 3px;
         left: 3px;
         width: 20px;
         height: 20px;
         background: var(--white);
         border-radius: 50%;
         transition: transform 0.3s ease;
         box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
         }
         .toggle.active .toggle-knob {
         transform: translateX(22px);
         }
         .reset-confirm {
         display: none;
         position: fixed;
         top: 0;
         left: 0;
         right: 0;
         bottom: 0;
         background: rgba(255, 255, 255, 0.9);
         backdrop-filter: blur(8px);
         z-index: 100;
         align-items: center;
         justify-content: center;
         padding: 24px;
         }
         .reset-confirm.show {
         display: flex;
         }
         .confirm-card {
         background: var(--white);
         border-radius: 24px;
         padding: 32px;
         max-width: 320px;
         text-align: center;
         box-shadow: var(--shadow-medium);
         animation: slideUp 0.3s ease-out;
         }
         .confirm-card h3 {
         font-size: 1.25rem;
         font-weight: 600;
         color: var(--gray-700);
         margin-bottom: 12px;
         }
         .confirm-card p {
         font-size: 0.875rem;
         color: var(--gray-500);
         margin-bottom: 24px;
         }
         .confirm-actions {
         display: flex;
         gap: 12px;
         }
         .confirm-actions .btn {
         flex: 1;
         }
         .btn-cancel {
         background: var(--pink-50);
         color: var(--gray-600);
         }
         .btn-confirm {
         background: var(--pink-500);
         color: var(--white);
         }
         .footer {
         margin-top: 48px;
         font-size: 0.75rem;
         color: var(--pink-400);
         opacity: 0;
         animation: fadeIn 0.8s ease-out 0.8s forwards;
         }
         @keyframes fadeIn {
         from { opacity: 0; }
         to { opacity: 1; }
         }
         @keyframes slideUp {
         from {
         opacity: 0;
         transform: translateY(20px);
         }
         to {
         opacity: 1;
         transform: translateY(0);
         }
         }
         @keyframes popIn {
         from {
         opacity: 0;
         transform: scale(0.9);
         }
         to {
         opacity: 1;
         transform: scale(1);
         }
         }
         @keyframes countUp {
         from { opacity: 0; transform: translateY(10px); }
         to { opacity: 1; transform: translateY(0); }
         }
         .counting .day-number {
         animation: countUp 0.3s ease-out;
         }
         /* Mobile optimizations */
         @media (max-width: 380px) {
         .day-number {
         font-size: 5rem;
         }
         .counter-card {
         padding: 36px 24px;
         }
         }
         /* Reduced motion preference */
         @media (prefers-reduced-motion: reduce) {
         *, *::before, *::after {
         animation-duration: 0.01ms !important;
         animation-iteration-count: 1 !important;
         transition-duration: 0.01ms !important;
         }
         }
         #calendarGrid {
         display: grid;
         grid-template-columns: repeat(7, 36px);
         gap: 8px;
         justify-content: center;
         }
         .calendar-day {
         width: 36px;
         height: 36px;
         display: flex;
         align-items: center;
         justify-content: center;
         border-radius: 12px;
         font-size: 14px;
         background: var(--pink-100);
         color: var(--text-dark);
         cursor: pointer;
         user-select: none;
         }
         .calendar-day.checked {
         background: var(--pink-300);
         color: white;
         }
         .calendar-day.empty {
         visibility: hidden;
         }
         .toggle-column {
         display: flex;
         flex-direction: column;
         gap: 12px;
         }
         #dailyNote {
         width: 100%;
         margin-top: 12px;
         padding: 12px;
         border-radius: 12px;
         border: 1px solid var(--pink-50);
         font-family: inherit;
         font-size: 0.85rem;
         resize: none;
         }
         .calendar-day.past-day {
         background: var(--pink-300);
         }
         .calendar-day.checked {
         background: var(--pink-500);
         }
         .calendar-day.selected {
         outline: 2px solid var(--pink-500);
         }
      </style>
   </head>
   <body>
      <div class="container">
         <header class="header">
            <h1>super cool vape tracker</h1>
            <p>for my pretty girl <3</p>
         </header>
         <main class="counter-card" id="counterCard">
            <div class="day-number" id="dayCount">0</div>
            <div class="day-label">days vape-free</div>
            <div class="sub-time" id="subTime"></div>
            <div class="encouragement" id="encouragement">You've got this 💗</div>
            <div class="milestone-badge hidden" id="milestone">
               <span>🏆</span>
               <span id="milestoneText"></span>
            </div>
         </main>
         <section class="settings">
            <div class="toggle-column">
               <div class="toggle-row">
                  <span>Daily motivation</span>
                  <div class="toggle active" id="motivationToggle">
                     <div class="toggle-knob"></div>
                  </div>
               </div>
               <button class="btn btn-secondary" id="openCalendar">
               📅 view calendar
               </button>
            </div>
         </section>
         <div class="reset-confirm" id="calendarModal">
            <div class="confirm-card">
               <h3 id="calendarTitle"></h3>
               <div id="calendarGrid"></div>
               <textarea
                  id="dailyNote"
                  placeholder="click a day to see or write how you felt"
                  rows="3"
                  ></textarea>
               <button class="btn btn-primary" id="saveNote">
               save note
               </button>
               <button class="btn btn-secondary" id="closeCalendar">
               close
               </button>
            </div>
         </div>
      </div>
      <script>
         const state = {
             startDate: null,
             motivationEnabled: true,
             currentDays: 0,
             notes: {}
         };
         
         const messages = {
             start: [
                 "okay. day 1. this is kinda big 💗",
                 "YOU STARTED. proud of u already",
                 "first day down… you've got this baby 🌸"
             ],
         
             early: [
                 "okay wait you’re actually doing really well",
                 "i believe in you!!!",
                 "stay strong ily",
                 "you're doing so well"
             ],
         
             week: [
                 "A WHOLE WEEK??? GOOD JOB",
                 "baby 7 days is AMAZING MWAHHH 💗",
                 "i'm so proud of you i love you 🌸"
             ],
         
             progress: [
                 "you're so strong omds, i'm so proud of you",
                 "the days will add up and up and up",
                 "you're doing SOOOO WELL 💗",
                 "you’re stronger than you think baby"
             ],
         
             milestone: [
                 "OH MILESTONE??? I SEE YOU 🏆",
                 "you better not downplay this",
                 "IM SO PROUDDDD UGHHHGHGH"
             ]
         };
         
         const milestones = [
             { days: 1, text: "First day done!" },
             { days: 3, text: "3 days!" },
             { days: 7, text: "One week milestone!" },
             { days: 14, text: "Two weeks!" },
             { days: 30, text: "30 days - WOW!" },
             { days: 60, text: "60 days - 60 DAYS????!" },
             { days: 90, text: "90 days - okay yea do u even need this anymore..." },
             { days: 180, text: "6 months - you go baby" },
             { days: 365, text: "One year - I LOVE YOUUUUU" }
         ];
         
         const elements = {
             dayCount: document.getElementById('dayCount'),
             encouragement: document.getElementById('encouragement'),
             milestone: document.getElementById('milestone'),
             milestoneText: document.getElementById('milestoneText'),
             //startBtn: document.getElementById('startBtn'),
             resetBtn: document.getElementById('resetBtn'),
             motivationToggle: document.getElementById('motivationToggle'),
             //resetConfirm: document.getElementById('resetConfirm'),
             cancelReset: document.getElementById('cancelReset'),
             confirmReset: document.getElementById('confirmReset'),
             counterCard: document.getElementById('counterCard'),
             calendarModal: document.getElementById('calendarModal'),
             calendarGrid: document.getElementById('calendarGrid'),
             calendarTitle: document.getElementById('calendarTitle'),
         };
         
         let currentMonth = new Date();
         
         const STORAGE_KEYS = {
             startDate: 'vapeFree_startDate',
             motivation: 'vapeFree_motivation',
             notes: 'vapeFree_notes'
         };
         
         function init() {
             loadState();
             setupEventListeners();
             updateUI();
         }
         
         function loadState() {
             const savedDate = localStorage.getItem(STORAGE_KEYS.startDate);
             const savedMotivation = localStorage.getItem(STORAGE_KEYS.motivation);
             const savedNotes = localStorage.getItem(STORAGE_KEYS.notes);
             state.notes = savedNotes ? JSON.parse(savedNotes) : {};
         
             if (savedDate) {
                 state.startDate = new Date(savedDate);
             } else {
                 const startDate = new Date(2026, 1, 4); 
                 startDate.setHours(1, 0, 0, 0);
                 state.startDate = startDate;
                 saveState();
             }
         
             if (savedMotivation !== null) {
                 state.motivationEnabled = savedMotivation === 'true';
                 elements.motivationToggle.classList.toggle('active', state.motivationEnabled);
             }
         }
         
         function saveState() {
             if (state.startDate) {
                 localStorage.setItem(STORAGE_KEYS.startDate, state.startDate.toISOString());
             } else {
                 localStorage.removeItem(STORAGE_KEYS.startDate);
             }
             localStorage.setItem(STORAGE_KEYS.motivation, state.motivationEnabled);
             localStorage.setItem(STORAGE_KEYS.notes, JSON.stringify(state.notes));
         }
         
         function calculateTime() {
             if (!state.startDate) return { days: 0, hours: 0, minutes: 0 };
         
             const now = new Date();
             const diffMs = now - state.startDate;
         
             const totalMinutes = Math.floor(diffMs / (1000 * 60));
             const days = Math.floor(totalMinutes / (60 * 24));
             const hours = Math.floor((totalMinutes % (60 * 24)) / 60);
             const minutes = totalMinutes % 60;
         
             return { days: Math.max(0, days), hours, minutes };
         }
         
         function getMessage(days) {
             if (!state.motivationEnabled) return '';
             
             if (days === 0) {
                 return randomFrom(messages.start);
             } else if (days < 7) {
                 return randomFrom(messages.early);
             } else if (days === 7) {
                 return randomFrom(messages.week);
             } else if (isMilestone(days)) {
                 return randomFrom(messages.milestone);
             } else {
                 return randomFrom(messages.progress);
             }
         }
         
         function isMilestone(days) {
             return milestones.some(m => m.days === days);
         }
         
         function getMilestoneText(days) {
             const milestone = milestones.find(m => m.days === days);
             return milestone ? milestone.text : '';
         }
         
         function randomFrom(arr) {
             return arr[Math.floor(Math.random() * arr.length)];
         }
         
         function animateCount(targetNumber) {
             const duration = 800;
             const startTime = performance.now();
             const startNumber = 0;
             
             elements.counterCard.classList.add('counting');
             
             function update(currentTime) {
                 const elapsed = currentTime - startTime;
                 const progress = Math.min(elapsed / duration, 1);
                 
                 const easeOutQuart = 1 - Math.pow(1 - progress, 4);
                 const current = Math.floor(startNumber + (targetNumber - startNumber) * easeOutQuart);
                 
                 elements.dayCount.textContent = current;
                 
                 if (progress < 1) {
                     requestAnimationFrame(update);
                 } else {
                     elements.dayCount.textContent = targetNumber;
                     elements.counterCard.classList.remove('counting');
                 }
             }
             
             requestAnimationFrame(update);
         }
         
         function openCalendar() {
         renderCalendar();
         
         const today = new Date();
         const key = `${today.getFullYear()}-${today.getMonth() + 1}-${today.getDate()}`;
         
         const noteBox = document.getElementById('dailyNote');
         noteBox.value = state.notes[key] || '';
         noteBox.dataset.date = key;
         
         elements.calendarModal.classList.add('show');
         }
         
         
         function closeCalendar() {
             elements.calendarModal.classList.remove('show');
         }
         
         function renderCalendar() {
             elements.calendarGrid.innerHTML = '';
         
             const year = currentMonth.getFullYear();
             const month = currentMonth.getMonth();
         
             elements.calendarTitle.textContent = currentMonth.toLocaleString('default', {
                 month: 'long',
                 year: 'numeric'
             });
         
             const firstDay = new Date(year, month, 1).getDay();
             const daysInMonth = new Date(year, month + 1, 0).getDate();
         
             for (let i = 0; i < firstDay; i++) {
                 const empty = document.createElement('div');
                 empty.className = 'calendar-day empty';
                 elements.calendarGrid.appendChild(empty);
             }
         
             for (let day = 1; day <= daysInMonth; day++) {
                 const dateKey = `${year}-${month + 1}-${day}`;
                 const cell = document.createElement('div');
                 cell.className = 'calendar-day';
         
                 if (state.notes[dateKey]) {
                     cell.classList.add('checked');
                 }
         
                 cell.textContent = day;
         
                 const today = new Date();
         today.setHours(0,0,0,0);
         
         const cellDate = new Date(year, month, day);
         
         if (cellDate <= today) {
         cell.classList.add('past-day');
         }
         
         cell.onclick = () => {
         document
         .querySelectorAll('.calendar-day.selected')
         .forEach(d => d.classList.remove('selected'));
         
         cell.classList.add('selected');
         
         const noteBox = document.getElementById('dailyNote');
         noteBox.value = state.notes[dateKey] || '';
         noteBox.dataset.date = dateKey;
         };
         
         
         
                 elements.calendarGrid.appendChild(cell);
             }
         }
         
         function updateUI() {
             const time = calculateTime();
             const days = time.days;
             state.currentDays = days;
         
             const subTimeEl = document.getElementById('subTime');
         
             if (days > 0 && (time.hours > 0 || time.minutes > 0)) {
         subTimeEl.textContent = `+ ${time.hours}h ${time.minutes}m`;
         } else {
         subTimeEl.textContent = '';
         }
         
         
             animateCount(days);
             
             elements.encouragement.textContent = getMessage(days);
             
             const milestoneText = getMilestoneText(days);
             if (milestoneText && days > 0) {
                 elements.milestoneText.textContent = milestoneText;
                 elements.milestone.classList.remove('hidden');
             } else {
                 elements.milestone.classList.add('hidden');
             }
         }
         
         function setupEventListeners() {
             elements.motivationToggle.addEventListener('click', () => {
                 state.motivationEnabled = !state.motivationEnabled;
                 elements.motivationToggle.classList.toggle('active', state.motivationEnabled);
                 saveState();
                 updateUI();
             });
         
             document.getElementById('openCalendar').addEventListener('click', openCalendar);
             document.getElementById('closeCalendar').addEventListener('click', closeCalendar);
         
             document.getElementById('saveNote').addEventListener('click', () => {
         const noteBox = document.getElementById('dailyNote');
         const dateKey = noteBox.dataset.date;
         
         if (!dateKey) return;
         
         if (noteBox.value.trim() !== '') {
         state.notes[dateKey] = noteBox.value.trim();
         } else {
         delete state.notes[dateKey];
         }
         
         saveState();
         renderCalendar();
         });

         }
         
         init();
      </script>
   </body>
</html>
