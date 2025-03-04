# MyFuelFinder
FuelFinder for Can

//   // Map initialization
    //   const map = L.map(document.querySelector('.map-container'), {
    //     attributionControl: false,  // Deactivate standard attribution data
    //     zoomControl:        false   // Deactivate standard zoom option
    //   }).setView([47.7819, 9.6136], 14);

    //   // OSM layer
    //   L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    //     maxZoom: 20,
    //     attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
    //   }).addTo(map);


    //   if(!navigator.geolocation) {
    //     console.log("Your browser doesn´t support geolocation feature");
    //   } else {
    //     setInterval(()  => {
    //       navigator.geolocation.getCurrentPosition(getPosition)
    //     }, 10000);
    //   }

    //   function getPosition(position) {
    //     // console.log(position);
    //     var latitude =  position.coords.latitude;
    //     var longitude = position.coords.longitude;
    //     var accuracy  = position.coords.accuracy;

    //     var circle  = L.circle([latitude, longitude], {radius: accuracy}).addTo(map);
    //     console.log(latitude, longitude, accuracy);
    //   }

    //   // Zoom controll options
    //   L.control.zoom({
    //   position: 'bottomleft'
    //   }).addTo(map);

    //   // Scale controll options
    //   L.control.scale({
    //   metric:   true,
    //   imperial: false,
    //   position: 'bottomright'
    //   }).addTo(map);

    //   //Marker
    //   var gasIcon = L.icon({
    //     iconUrl:  gasIconUrl,
    //     iconSize: [20, 20],
    //   });

    //   var marker = L.marker([47.7819, 9.6136], { icon: gasIcon }).addTo(map);
    //   marker.bindPopup('This is a Test'); //Feature group verwenden, da viele marker kommen werden und dadurch ich einmalig alle behandeln kann

    //   setTimeout(() => {
    //   map.invalidateSize();
    // }, 100);