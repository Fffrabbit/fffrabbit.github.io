---
layout: default
title: Ylioppilastutkinnon tulosanalyysi – Petteri Kuisma
description: KMeans-klusterointianalyysi kevään 2025 ylioppilastutkinnon tuloksista. 25 901 kokelaan aineistosta viisi opiskelijaprofiilia, visualisoitu PCA:lla.
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

## Monivuotinen trendi (2020–2026)

Yllä oleva analyysi kattaa vain kevään 2025 tulokset. Jotta nähdään, ovatko ainevalintaprofiilit muuttuneet ajan myötä, sama menetelmä toistettiin yhdistämällä vuosien 2020–2026 kevään tulokset yhdeksi aineistoksi ja ajamalla klusterointi kerran koko datalle. Tärkeänä erona, jos klusterointi ajettaisiin erikseen joka vuodelle, klusterien numerointi ja sisältö eivät olisi vertailukelpoisia vuosien välillä.

![Ainevalintaprofiilien osuudet 2020–2026]({{ site.baseurl }}/assets/img/yo-tulkinta/trendi_2020_2026.png)

Selkeimpiä havaintoja on luonnontiede/lääke -profiilin ja laaja-alaisen pitkän matematiikan laskusuunta. Kun yhteiskuntaoppi ja terveys/psykologia painoisilla nähdään noususuuntaa. 

Luonnontiede/lääke-profiilin (pitkä matematiikka, kemia, fysiikka, biologia) osuus on laskenut tasaisesti 22 %:sta 17 %:iin vuosina 2020–2026, samalla kun yhteiskuntaoppipainotteisen profiilin (lyhyt matematiikka, yhteiskuntaoppi) osuus on noussut 17 %:sta 23 %:iin.

On syytä huomauttaa, että tämä on kuvaileva havainto, ei selitys. Data ei kerro, johtuuko muutos esimerkiksi lukiovalinnoista, opetussuunnitelman uudistuksesta vai jostain muusta.
