<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>

<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

<!-- Latest compiled and minified JavaScript -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

# Lekarstwa

## Waga

<label for="waga" class="form-label">Waga</label>
<input type="range" class="form-range" min="3" max="40" id="waga">

<div id="infwaga">Waga to: </div>


## Amotaks

<div id="amotaks">Dawka dobowa od 50 do 90 mg/kg. Podajemy w 3 dawkach. 100 mg jest w 1 ml. </div>
<div id="amotaksinfo"> </div>

## Ospen

<div id="ospen">Dawka dobowa od 50 tys do 100 tys/kg. Podajemy w 3 dawkach. 750 tys jest w 5 ml, czyli 150 tys jest w 1 ml. </div>
<div id="ospeninfo"> </div>

## Klacid

<div id="klacid">Dawka dobowa 7.5 mg/kg. Podajemy w 2 dawkach maksymalnie 500 mg x 2 na dobę. Roztwór ma 25 mg w 1 ml lub 50 mg w 1 ml. </div>
<div id="klacidinfo"> </div>

## Augmentin ES

<div id="augmentin">Dawka dobowa 90 + 6.4 mg/kg. Podajemy w 2 dawkach. Roztwór ma 128.58 mg w 1 ml. </div>
<div id="augmentininfo"> </div>

## Bactrim

<div id="butrim">Dawka dobowa 36 mg/kg. Podajemy w 2 dawkach. Roztwór ma 48 mg w 1 ml. </div>
<div id="butriminfo"> </div>


## Zinnat

<div id="zinnat">Dawka dobowa 15 mg/kg. Podajemy w 2 dawkach maksymalnie 250 mg x 2 na dobę. Roztwór ma 25 mg w 1 ml lub 50 mg w 1 ml. </div>
<div id="zinnatinfo"> </div>


## Cetix

<div id="cetix">Dawka dobowa 8 mg/kg. Podajemy w 2 dawkach maksymalnie 100 mg x 2 na dobę. Roztwór ma 20 mg w 1 ml. </div>
<div id="cetixinfo"> </div>


## Furazek

<div id="furazek">Dawka dobowa od 5 do 7 mg/kg. Podajemy w 2 dawkach. 10 mg jest w 1 ml. </div>
<div id="furazekinfo"> </div>


<script>

function round2(v){
  return Math.round(v*100.0)/100.0;
}

function updateMeds(v){
    const result = document.querySelector('div#infwaga');
  result.textContent = `Podana waga to: ${v}`;

  const amotaksinfo = document.querySelector('div#amotaksinfo');
  amotaksinfo.textContent = `Min: ${round2(v*50/3.0)}, maks: ${round2(v*90/3.0)} mg na dawkę czyli min ${round2(v*50/3.0/100.0)} maks ${round2(v*90/3.0/100.0)} ml na dawkę.`;

  const ospeninfo = document.querySelector('div#ospeninfo');
  ospeninfo.textContent = `Min: ${round2(v*50/3.0)}, maks: ${round2(v*100/3.0)} mg na dawkę czyli min ${round2(v*50/3.0/150.0)} maks ${round2(v*100/3.0/150.0)} ml na dawkę`;

  klacidmax = Math.min(v*7.5/2.0, 500.0);
  const klacidinfo = document.querySelector('div#klacidinfo');
  klacidinfo.textContent = `Wychodzi: ${round2(v*7.5/2.0)}, po uwzględnieniu zasady maks 500 mg x 2 na dobę: ${round2(klacidmax)} mg na dawkę. Dla roztworu 25 mg - 1 ml: ${round2(klacidmax/25.0)} ml na dawkę. Dla roztworu 50 mg - 1 ml: ${round2(klacidmax/50.0)} ml na dawkę.`;

  const augmentininfo = document.querySelector('div#augmentininfo');
  augmentininfo.textContent = `Wychodzi: ${round2(v*(90+6.4)/2.0)} mg na dawkę, czyli ${round2(v*96.4/2.0/128.58)} ml na dawkę.`;

  const butriminfo = document.querySelector('div#butriminfo');
  butriminfo.textContent = `Wychodzi: ${round2(v*(36)/2.0)} mg na dawkę, czyli ${round2(v*36.0/2.0/48.0)} ml na dawkę.`;


  zinnatmax = Math.min(v*15/2.0, 250.0);
  const zinnatinfo = document.querySelector('div#zinnatinfo');
  zinnatinfo.textContent = `Wychodzi: ${round2(v*15/2.0)}, po uwzględnieniu zasady maks 250 mg x 2 na dobę: ${round2(zinnatmax)} mg na dawkę. Dla roztworu 25 mg - 1 ml: ${round2(zinnatmax/25.0)} ml na dawkę. Dla roztworu 50 mg - 1 ml: ${round2(zinnatmax/50.0)} ml na dawkę.`;


  const furazekinfo = document.querySelector('div#furazekinfo');
  furazekinfo.textContent = `Min: ${round2(v*5/2.0)}, maks: ${round2(v*7/2.0)} mg na dawkę czyli min ${round2(v*5/2.0/10.0)} maks ${round2(v*7/2.0/10.0)} ml na dawkę.`;

    cetixmax = Math.min(v*8/2.0, 100.0);
  const cetixinfo = document.querySelector('div#cetixinfo');
  cetixinfo.textContent = `Wychodzi: ${round2(v*8/2.0)}, po uwzględnieniu zasady maks 100 mg x 2 na dobę: ${round2(cetixmax)} mg na dawkę, czyli ${round2(cetixmax/20.0)} ml na dawkę.`;

}

window.addEventListener('load', (event) => {
  updateMeds(document.querySelector('input#waga.form-range').value);
});

const selectElement = document.querySelector('input#waga.form-range');
selectElement.addEventListener('change', (event) => {
  v = event.target.value;
  updateMeds(v);
});
</script>


