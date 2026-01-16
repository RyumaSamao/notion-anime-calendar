<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prototype Calendrier Anime</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #f2f2f2;
    display: flex;
    justify-content: center;
    padding: 20px;
  }
  .calendar {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
    max-width: 900px;
    width: 100%;
  }
  .day {
    background: white;
    padding: 10px;
    min-height: 100px;
    border-radius: 8px;
    position: relative;
    cursor: pointer;
    transition: transform 0.1s;
  }
  .day:hover {
    transform: scale(1.03);
    box-shadow: 0 2px 10px rgba(0,0,0,0.2);
  }
  .day-number {
    font-weight: bold;
    margin-bottom: 5px;
  }
  .anime-list {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    width: 250px;
    background: #fff;
    border: 1px solid #ddd;
    padding: 10px;
    z-index: 10;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2);
  }
  .anime-item {
    margin-bottom: 5px;
    padding: 5px;
    border-left: 4px solid #3498db;
  }
  .close-btn {
    float: right;
    cursor: pointer;
    font-weight: bold;
    color: #888;
  }
  .weekday {
    text-align: center;
    font-weight: bold;
    margin-bottom: 5px;
  }
</style>
</head>
<body>

<div class="calendar-container">
  <div class="calendar-weekdays">
    <div class="weekday">Lun</div>
    <div class="weekday">Mar</div>
    <div class="weekday">Mer</div>
    <div class="weekday">Jeu</div>
    <div class="weekday">Ven</div>
    <div class="weekday">Sam</div>
    <div class="weekday">Dim</div>
  </div>
  <div class="calendar" id="calendar"></div>
</div>

<script>
  // Données fictives
  const animeData = [
    { title: "Jujutsu Kaisen", date: "2026-01-16", time: "19:00", ep: 2 },
    { title: "One Piece", date: "2026-01-18", time: "10:00", ep: 1015 },
    { title: "Frieren", date: "2026-01-20", time: "20:00", ep: 1 },
    { title: "Naruto Shippuden", date: "2026-01-25", time: "21:00", ep: 400 }
  ];

  const calendarEl = document.getElementById("calendar");
  const today = new Date("2026-01-01"); // Mois fictif janvier 2026
  const year = today.getFullYear();
  const month = today.getMonth();

  // Nombre de jours dans le mois
  const daysInMonth = new Date(year, month + 1, 0).getDate();

  // Jour du premier jour du mois (0 = dimanche, 1 = lundi)
  const firstDay = new Date(year, month, 1).getDay();
  const offset = firstDay === 0 ? 6 : firstDay - 1; // ajuster pour que lundi soit premier jour

  // Générer les cases du calendrier
  for (let i = 0; i < offset + daysInMonth; i++) {
    const dayEl = document.createElement("div");
    dayEl.className = "day";
    if (i >= offset) {
      const dayNum = i - offset + 1;
      dayEl.innerHTML = `<div class="day-number">${dayNum}</div>`;
      
      // Vérifier si des animes sortent ce jour
      const dateStr = `${year}-${String(month+1).padStart(2,"0")}-${String(dayNum).padStart(2,"0")}`;
      const animeToday = animeData.filter(a => a.date === dateStr);
      
      if(animeToday.length > 0){
        const animeListEl = document.createElement("div");
        animeListEl.className = "anime-list";
        animeToday.forEach(a => {
          const item = document.createElement("div");
          item.className = "anime-item";
          item.innerHTML = `<strong>${a.title}</strong> - Ep ${a.ep} <br> ${a.time}`;
          animeListEl.appendChild(item);
        });
        const closeBtn = document.createElement("div");
        closeBtn.className = "close-btn";
        closeBtn.innerText = "x";
        closeBtn.onclick = (e)=>{
          e.stopPropagation();
          animeListEl.style.display="none";
        };
        animeListEl.prepend(closeBtn);
        dayEl.appendChild(animeListEl);
        
        dayEl.onclick = () => {
          animeListEl.style.display = animeListEl.style.display === "block" ? "none" : "block";
        };
      }
    }
    calendarEl.appendChild(dayEl);
  }
</script>

</body>
</html>
