---
layout: default
title: YO-tulkinta
---

# YO-tulkinta (2025K)

Analyysi ylioppilastutkinnon kevään 2025 tulosdatasta oppimisanalytiikan näkökulmasta. Aineistona Ylioppilastutkintolautakunnan avoin data (FT2025KD3001.csv), joka sisältää kaikkien kevään 2025 ylioppilaiden (25 901 kokelasta) kokeiden arvosanat kokelaskohtaisesti, ilman nimitietoja.

## Menetelmä

Sen sijaan että tarkastellaan arvosanoja, tässä tarkastellaan mitä aineita kokelaat valitsivat kirjoitettavaksi. Kokelaista muodostettiin binäärimatriisi (kirjoitti/ei kirjoittanut kutakin ainetta) ja tälle ajettiin KMeans-klusterointi, jotta aineistosta nousee luonnollisia ainevalintaprofiileja ilman että profiilit määritellään etukäteen.

Ensimmäinen klusterointiyritys sisälsi kieleen sidottuja aineita (äidinkieli, pitkä englanti, ruotsi/suomi toisena kielenä), jotka ovat käytännössä pakollisia lähes kaikille eivätkä kerro yksilön kiinnostuksesta. Tämä näkyi tuloksissa niin, että klusterit erottuivat lähinnä opetuskielen (suomi/ruotsi) perusteella, ei aidosta ainevalinnasta. Nämä aineet poistettiin ja klusterointi ajettiin uudestaan, jolloin profiilit alkoivat erottua reaaliainepainotusten perusteella.

## Tulokset

Analyysi tuotti viisi profiilia. Suurin jakolinja on pitkän ja lyhyen matematiikan välillä, ja sen sisällä profiilit erottuvat reaaliainepainotuksen mukaan:

- **Luonnontiede/lääke** (pitkä matematiikka): biologia, kemia ja fysiikka vahvasti edustettuina
- **Fysiikka/yhteiskunta** (pitkä matematiikka): fysiikkaa ja yhteiskuntaoppia, ei yhtä vahvaa biologia/kemia-painotusta
- **Terveystietopainotteinen** (lyhyt matematiikka)
- **Yhteiskuntaoppipainotteinen** (lyhyt matematiikka)
- **Yleisreaali** (lyhyt matematiikka): hajanaisempi, ei yhtä dominoivaa ainetta

Profiilit visualisoitiin PCA-projektiolla kahteen ulottuvuuteen (yhteensä 41 % selitetystä varianssista):

![Ainevalintaprofiilit PCA-projektiona]({{ site.baseurl }}/assets/img/yo-tulkinta/pca_klusterit-2.png)

Kuvasta erottuvat selkeimmin pitkän matematiikan klusterit omiksi tiiviiksi ryhmikseen, kun taas lyhyen matematiikan klusterit menevät osittain päällekkäin – tämä on odotettua, koska ne erottuvat toisistaan asteittaisen reaaliainepainotuksen eikä yhden selkeän muuttujan perusteella.
