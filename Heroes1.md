
### Heroes Of Pymoli Data Analysis
* Of the 1163 active players, the vast majority are male (84%). There also exists, a smaller, but notable proportion of female players (14%).

* Our peak age demographic falls between 20-24 (44.8%) with secondary groups falling between 15-19 (18.60%) and 25-29 (13.4%).  
-----

### Note
* Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.


```python
# Dependencies and Setup
import pandas as pd
import numpy as np

# File to Load (Remember to Change These)
heros = "Resources/purchase_data.csv"

# Read Purchasing File and store into Pandas data frame
heros = pd.read_csv(heros)
```

## Player Count

* Display the total number of players



```python
heros.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
    </tr>
  </tbody>
</table>
</div>




```python
count = heros["SN"].value_counts()
count
```




    Lisosia93          5
    Idastidru52        4
    Iral74             4
    Phaena87           3
    Aelin32            3
    Lisim78            3
    Siallylis44        3
    Phyali88           3
    Umolrian85         3
    Haillyrgue51       3
    Yathecal82         3
    Raesty92           3
    Lisopela58         3
    Ilarin91           3
    Asur53             3
    Iskadarya95        3
    Idai61             3
    Hiaral50           3
    Aina42             3
    Ialallo29          3
    Tyidaim51          3
    Lassilsala30       3
    Chadolyla44        3
    Inguron55          3
    Sondastsda82       3
    Saedaiphos46       3
    Rarallo90          3
    Hada39             3
    Chanastnya43       3
    Chamimla85         3
                      ..
    Malarrian73        1
    Lisassa64          1
    Eurisuru25         1
    Aelaria33          1
    Tyeurith29         1
    Chanilsasda38      1
    Lisirra87          1
    Aiduesu86          1
    Assehoan67         1
    Frichossala54      1
    Chamalo71          1
    Aela59             1
    Ennalmol65         1
    Syathe73           1
    Aerithriaphos45    1
    Sisur91            1
    Yalo85             1
    Tyaedainu44        1
    Iskosia90          1
    Peorith44          1
    Undirrasta89       1
    Ardonmol96         1
    Asty82             1
    Siana77            1
    Chanosiaya39       1
    Thryallym62        1
    Mindimnya67        1
    Lisico81           1
    Ingatcil75         1
    Iduelis31          1
    Name: SN, Length: 576, dtype: int64




```python
total= [{"Total Players": 576}]

total_players = pd.DataFrame(total)
total_players

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>576</td>
    </tr>
  </tbody>
</table>
</div>




```python
heros.head()
unique = heros["SN"].unique()
unique
```




    array(['Lisim78', 'Lisovynya38', 'Ithergue48', 'Chamassasya86',
           'Iskosia90', 'Yalae81', 'Itheria73', 'Iskjaskst81', 'Undjask33',
           'Chanosian48', 'Inguron55', 'Haisrisuir60', 'Saelaephos52',
           'Assjaskan73', 'Saesrideu94', 'Lisassa64', 'Lisirra25',
           'Zontibe81', 'Reunasu60', 'Chamalo71', 'Iathenudil29',
           'Phiarithdeu40', 'Siarithria38', 'Eyrian71', 'Siala43',
           'Lisirra87', 'Lirtossa84', 'Eusri44', 'Aela59', 'Tyida79',
           'Idai61', 'Farusrian86', 'Aeralria27', 'Haillyrgue51', 'Sondim73',
           'Jeyciman68', 'Idaisuir85', 'Seuthep89', 'Reulae52',
           'Sondilsaya62', 'Aerithriaphos45', 'Assosia88', 'Aidaillodeu39',
           'Aelly27', 'Tyeosri53', 'Haerith37', 'Yasrisu92', 'Chanuchi25',
           'Asur96', 'Iaralrgue74', 'Chanosia34', 'Aelin32', 'Ilosianya35',
           'Zhisrisu83', 'Phaelap26', 'Raesty92', 'Palyon91', 'Tyisur83',
           'Yaliru88', 'Yadanu52', 'Jiskimya77', 'Yadaphos40', 'Alo38',
           'Phaena87', 'Chamirraya83', 'Chanastsda67', 'Indonmol95',
           'Jiskossa61', 'Pheodai94', 'Hari50', 'Marilsa69', 'Assistasda42',
           'Lisosia93', 'Philodil43', 'Mindadaran26', 'Lirtosia63',
           'Assjaskan56', 'Irithlis29', 'Heudai45', 'Haerithp41', 'Aina42',
           'Jiskjask60', 'Umolrian85', 'Qarirwen82', 'Laedallo55',
           'Eoralrap26', 'Undosian34', 'Chadolyla44', 'Chadistaya75',
           'Yathedeu43', 'Aina43', 'Ilassast39', 'Lisassala98', 'Aiduecal76',
           'Chadossa89', 'Pheodaisun84', 'Heollyriap59', 'Maropast28',
           'Frichim77', 'Thryallym62', 'Eulanurin88', 'Lassjaskan73',
           'Tyaerith73', 'Sondadarya58', 'Hirirap39', 'Ririp86', 'Sundim98',
           'Iskichinya81', 'Phyali88', 'Undirrala66', 'Nitherian58',
           'Lassilsala30', 'Frichaststa61', 'Frichosia58', 'Ilosia37',
           'Lisista27', 'Seudaillorap38', 'Aesty53', 'Yathecal82',
           'Lisossanya98', 'Iral74', 'Lisast87', 'Maridisya31', 'Jiskassa76',
           'Ethriel85', 'Iskirra45', 'Iri67', 'Rarallo90', 'Lisasi93',
           'Adastirin33', 'Eyista89', 'Ili43', 'Chamirra53', 'Hailaphos89',
           'Iskadarya95', 'Qilatista90', 'Inasti31', 'Marilsanya48',
           'Marjask87', 'Chanjaskan89', 'Hyaduesu61', 'Aillyrin83',
           'Marast30', 'Sundadar27', 'Tyaelorap29', 'Lirtimst73',
           'Styaduen40', 'Sidap51', 'Chanastst38', 'Lirtassa52', 'Sondim68',
           'Aeral97', 'Heosurnuru52', 'Lisopela58', 'Caesrinusuir82',
           'Tyirinu79', 'Fironon91', 'Lassjask63', 'Indcil77', 'Chamimla73',
           'Syathe73', 'Baelollodeu94', 'Mindista32', 'Saena74',
           'Marirrasta50', 'Lamil79', 'Aenarap34', 'Aisur51', 'Thrientossa55',
           'Chadista79', 'Tyeurith29', 'Malunil62', 'Hiasri33', 'Lisadar44',
           'Frichjask31', 'Lisjaskya84', 'Ristydru66', 'Frichast28',
           'Minduri31', 'Maradaran90', 'Mindetosya30', 'Ialallo29',
           'Pheusrical25', 'Chanosia60', 'Phistym51', 'Aelollo59',
           'Chamimla85', 'Haisurra41', 'Sondastsda82', 'Qilanrion65',
           'Eulasuir89', 'Eosrirgue62', 'Shaidanu32', 'Lirtastan49',
           'Iaralsuir44', 'Tyeudariasuir90', 'Cosadar58', 'Aelastirin39',
           'Aidai53', 'Jiskjask85', 'Ealrion88', 'Chamjask73', 'Tyaenasti87',
           'Alim85', 'Haeladil46', 'Jiskirran77', 'Undosia27', 'Peorith44',
           'Yarithsurgue62', 'Taeduenu92', 'Rairin89', 'Aerithriaphos46',
           'Idairin51', 'Lisista54', 'Eodailis27', 'Lirtastsda29',
           'Undilsan50', 'Eodaisu60', 'Quaranmol58', 'Lirtossa60',
           'Lirtilsa71', 'Isursuir31', 'Sundirrala66', 'Saerallora71',
           'Iasur80', 'Tyaelo67', 'Quanunwen42', 'Yasur35', 'Assehoan67',
           'Haellysu29', 'Saida58', 'Chamadar79', 'Aeral43', 'Lirtirra37',
           'Tyidaim51', 'Lassassast73', 'Assassasta79', 'Heollyra92',
           'Anallorgue57', 'Aerithllora36', 'Smaistysu35', 'Ennalmol65',
           'Yarithrgue83', 'Yana46', 'Sondimla25', 'Aidai61', 'Wailin72',
           'Firan91', 'Alaesu91', 'Aellynun67', 'Rilaera56', 'Eulaestira36',
           'Marim28', 'Idastidru52', 'Ilirrasda54', 'Alaephos75',
           'Syalollorap93', 'Minduli80', 'Chanastya70', 'Frichadaran88',
           'Siallylis44', 'Aeri84', 'Iasursti71', 'Mindilsa34', 'Chamastya76',
           'Undirra73', 'Aestysu37', 'Chadadarla74', 'Strithenu87',
           'Iasrira89', 'Ialidru40', 'Tyalaesu89', 'Tyidainu31', 'Lirtilsa72',
           'Undjaskla97', 'Saedaiphos46', 'Aerithnucal56', 'Lisossa46',
           'Layjask75', 'Lisista63', 'Ceoral34', 'Hilaerin92',
           'Chadilsasta32', 'Undassa89', 'Iduenu77', 'Lisosia66',
           'Undimsya85', 'Phaedue89', 'Yadacal26', 'Lisossa25', 'Ilmol66',
           'Yastyriaphos75', 'Hiasurria41', 'Palatyon26', 'Qilalista41',
           'Hada39', 'Chamilsala65', 'Rairith81', 'Ilarin91', 'Ryanara76',
           'Undista85', 'Tyeoralru41', 'Pheosrinudeu70', 'Heuli25',
           'Pheutherin27', 'Chadirra90', 'Ali84', 'Frichjaskan98', 'Malil90',
           'Yarithllodeu72', 'Tyaedainu44', 'Ethron58', 'Eusurdeu49',
           'Saistyphos30', 'Saisrilis27', 'Hallysucal81', 'Ilimya66',
           'Raysistast71', 'Haedairiadru51', 'Tyananurgue44', 'Risty84',
           'Aerillorin70', 'Phistyn52', 'Yalo85', 'Chamirrasya33', 'Hiral75',
           'Isursti83', 'Bartassaya73', 'Aeda94', 'Quinarap53', 'Asur53',
           'Alarap40', 'Sida61', 'Hiarideu73', 'Lassassasda30', 'Ennoncil86',
           'Siralsudeu54', 'Eusri26', 'Ardcil81', 'Marilsasya33', 'Lirtim36',
           'Heunadil74', 'Frichadar89', 'Aesurstilis64', 'Idaidil28',
           'Lisotesta51', 'Lisico81', 'Lisiriya82', 'Siana77', 'Marokian45',
           'Sausosia74', 'Assesi91', 'Eusri70', 'Aisurria69', 'Iarilis73',
           'Raisty38', 'Ilista82', 'Leyirra83', 'Aiduesu86', 'Frichynde86',
           'Hisridru55', 'Chamossa77', 'Irillo49', 'Lirtastsya71',
           'Frichosiala98', 'Qilunan34', 'Quarrion42', 'Aisurdru79',
           'Hiaral50', 'Iarallo65', 'Sondassasya91', 'Chanossast57',
           'Chanjask65', 'Ethralista69', 'Sondistanya61', 'Eudanu32',
           'Euthe35', 'Lassimla92', 'Lisossala30', 'Eulae84', 'Chamadarnya73',
           'Eolan54', 'Assistasda90', 'Ennrian78', 'Undirrasta89',
           'Rianistast50', 'Undare39', 'Adairialis76', 'Aesur96',
           'Tyialisudeu65', 'Arirgue63', 'Sundadarla27', 'Eyircil84', 'Ina92',
           'Lirtistanya48', 'Marassa62', 'Mindossa76', 'Salilis27',
           'Sondossa69', 'Sundjask71', 'Errian63', 'Eurithphos97',
           'Raillydeu47', 'Malon70', 'Jiskimsda56', 'Marughi89', 'Ingatcil75',
           'Chanirrasta87', 'Alaesu77', 'Ermol76', 'Tyeuduen32', 'Firon67',
           'Iadueria43', 'Pheulidil31', 'Eodairu79', 'Frichocesta66',
           'Thourdirra92', 'Chanastnya43', 'Iskim96', 'Eulolis41',
           'Sastydeu50', 'Ilaesudil92', 'Yasur85', 'Aidain51',
           'Aerithnuphos61', 'Yalostiphos68', 'Meosridil82', 'Aillyriadru65',
           'Sally64', 'Lisim51', 'Isurria36', 'Silaera56', 'Leetirraya83',
           'Lirtirra81', 'Eryon48', 'Iana95', 'Sondassan80', 'Chanadar44',
           'Eosurdru76', 'Shidai42', 'Aesri53', 'Syally44', 'Jiskadarst60',
           'Sondadar26', 'Malarrian73', 'Maluncil97', 'Ilunyon70', 'Yadam35',
           'Dyally87', 'Pheosurllorin41', 'Frichaya88', 'Lassadarsda57',
           'Marynde90', 'Isri34', 'Assastnya25', 'Ardonmol96',
           'Lassirrasda85', 'Chadossa56', 'Poshilsa82', 'Yoishirrala98',
           'Sundista37', 'Ilassa51', 'Filurarn35', 'Phaestycal84', 'Irilis75',
           'Aeralstical35', 'Chanirrala39', 'Chanirra79', 'Assirra56',
           'Seolollo93', 'Iathem87', 'Iasurriacal29', 'Lisast98', 'Filrion59',
           'Halaecal66', 'Iskosian40', 'Ilastilis78', 'Seosrim97',
           'Farrian71', 'Rithe53', 'Frichossala54', 'Chamjaskya75',
           'Quanrion96', 'Tyaelaelis94', 'Quanenrian83', 'Chanirra64',
           'Yadaisuir65', 'Syathecal44', 'Arin32', 'Aelaria33', 'Assassa81',
           'Filrion83', 'Eoral49', 'Airi27', 'Eurisuru25', 'Liawista80',
           'Lisirra58', 'Chamadarsda63', 'Haestyphos66', 'Phaedasurap84',
           'Mindimnya67', 'Chadjask85', 'Eustyria89', 'Iskim66', 'Chamast86',
           'Lirtassan78', 'Ethrasyon38', 'Quilassa66', 'Lisassasda39',
           'Mindilsa60', 'Lalossa38', 'Chamistast30', 'Hariphos58',
           'Assilsan72', 'Inasuir29', 'Chanilsasda38', 'Mindesi74',
           'Ililsan66', 'Idacal95', 'Aeral68', 'Tyarithn67', 'Asty82',
           'Yalaeria91', 'Chadjask77', 'Ealiril69', 'Quaecjask96',
           'Firatan58', 'Yarolwen77', 'Tyaelistidru84', 'Yarithrin84',
           'Tyaelly53', 'Phiristi62', 'Ililsasya43', 'Aithelis62',
           'Undotesta33', 'Aelidru27', 'Chanossanya44', 'Maradarnya40',
           'Lisilsa62', 'Saena89', 'Chanilsast61', 'Sundassa93', 'Aidai73',
           'Indirrian56', 'Lisassasta50', 'Iduelis31', 'Chanosiaya39',
           'Assylla81', 'Aidaira26', 'Eudanu84', 'Chamiman85', 'Tyialisti80',
           'Marundi65', 'Eusur90', 'Mindirranya33', 'Phiallylis33', 'Isty55',
           'Frichilsa31', 'Chanista95', 'Aellyria80', 'Rastynusuir31',
           'Iljask75', 'Lisjaskan36', 'Mindjasksya61', 'Frichirranya75',
           'Ilast79', 'Eratiel90', 'Assim27', 'Irith83', 'Ilosian36',
           'Iskossasda43', 'Hala31', 'Jiskjask80', 'Aethedru70', 'Yathecal72',
           'Sisur91'], dtype=object)



## Purchasing Analysis (Total)

* Run basic calculations to obtain number of unique items, average price, etc.


* Create a summary data frame to hold the results


* Optional: give the displayed data cleaner formatting


* Display the summary data frame



```python
unique_items = heros["Item Name"].unique()
unique_items
```




    array(['Extraction, Quickblade Of Trembling Hands', 'Frenzied Scimitar',
           'Final Critic', 'Blindscythe', 'Fury', 'Dreamkiss',
           'Interrogator, Blood Blade of the Queen', 'Abyssal Shard',
           'Souleater', 'Ghastly Adamantite Protector',
           'Singed Onyx Warscythe', 'Renewed Skeletal Katana',
           "Bloodlord's Fetish", 'Bone Crushing Silver Skewer',
           'Deadline, Voice Of Subtlety', 'Second Chance', 'Devine',
           'Nirvana', 'Blazefury, Protector of Delusions',
           'Despair, Favor of Due Diligence',
           'Sun Strike, Jaws of Twisted Visions', 'Warped Fetish',
           'Severance', 'Persuasion',
           'Oathbreaker, Last Hope of the Breaking Storm', 'Demise',
           'Blood-Forged Skeletal Spine',
           'Stormbringer, Dark Blade of Ending Misery',
           'Shadow Strike, Glory of Ending Hope', 'Striker',
           'Wolf, Promise of the Moonwalker', "Faith's Scimitar",
           'Bonecarvin Battle Axe', 'Azurewrath', 'Vengeance Cleaver',
           'Haunted Bronzed Bludgeon', 'Ritual Mace', 'Blade of the Grave',
           'Thorn, Satchel of Dark Souls', "Winter's Bite",
           'Thorn, Conqueror of the Corrupted', "Reaper's Toll", 'Avenger',
           'Shadowsteel', 'Peacekeeper, Wit of Dark Magic', 'Suspension',
           'Amnesia', 'Soul Infused Crystal', 'Wolf',
           'Relentless Iron Skewer', 'Hero Cane', 'Arcane Gem', 'Dreamsong',
           'Darkheart', 'Hailstorm Shadowsteel Scythe',
           'Whistling Mithril Warblade', 'Foul Titanium Battle Axe',
           'Retribution Axe', 'Rusty Skull',
           'Riddle, Tribute of Ended Dreams', 'Chaos, Ender of the End',
           'Storm-Weaver, Slayer of Inception', 'Venom Claymore',
           'Emberling, Defender of Delusions', 'Netherbane', 'Dawn',
           'Primitive Blade', 'Dawne', 'Curved Axe',
           'Fate, Vengeance of Eternal Justice',
           'Lazarus, Terror of the Earth', 'Lightning, Etcher of the King',
           'Betrayal, Whisper of Grieving Widows', 'Exiled Doomblade',
           'Undead Crusader', 'Downfall, Scalpel Of The Emperor',
           'Sleepwalker', 'Eternal Cleaver',
           'Expiration, Warscythe Of Lost Worlds', 'Malificent Bag',
           'Mercy, Katana of Dismay', 'Orbit', 'Deathraze', 'Serenity',
           'Heartstriker, Legacy of the Light', 'Glimmer, Ender of the Moon',
           'Deluge, Edge of the West', 'Crucifer', 'Piece Maker',
           'Brutality Ivory Warmace', "Freak's Bite, Favor of Holy Might",
           'Yearning Crusher', 'Agatha', 'Fiery Glass Crusader', 'Splinter',
           'Verdict', 'Warped Iron Scimitar',
           'Darkheart, Butcher of the Champion', 'Purgatory, Gem of Regret',
           'Woeful Adamantite Claymore', 'Hopeless Ebon Dualblade',
           "Warmonger, Gift of Suffering's End", "Misery's End",
           'Phantomlight', 'Conqueror Adamantite Mace', "Dragon's Greatsword",
           'Stormcaller', 'Spada, Etcher of Hatred', "Twilight's Carver",
           'Putrid Fan', 'Blood Infused Guardian', 'Singed Scalpel',
           'Warped Diamond Crusader', 'Endbringer', 'Feral Katana', 'Orenmir',
           'Piety, Guardian of Riddles', 'Brimstone', 'Stormfury Mace',
           'Frenzy, Defender of the Harvest', "Solitude's Reaver",
           'Mercenary Sabre', 'Yearning Mageblade',
           'Tranquility, Razor of Black Magic',
           'Oathbreaker, Spellblade of Trials',
           'Aetherius, Boon of the Blessed', 'Righteous Might',
           'Victor Iron Spikes', 'Swan Song, Gouger Of Terror',
           'Thunderfury Scimitar', 'Splitter, Foe Of Subtlety',
           'Restored Bauble', 'The Decapitator',
           'Pursuit, Cudgel of Necromancy', 'Lifebender',
           'Flux, Destroyer of Due Diligence', 'Mourning Blade', 'Toothpick',
           "Hope's End", 'Torchlight, Bond of Storms', 'Thirsty Iron Reaver',
           'Stormfury Longsword', 'Malice, Legacy of the Queen',
           'War-Forged Gold Deflector', 'Blazeguard, Reach of Eternity',
           'Soul-Forged Steel Shortsword',
           'Hellreaver, Heirloom of Inception', 'Heartless Bone Dualblade',
           'Scalpel', 'Hatred', 'Crying Steel Sickle',
           'The Void, Vengeance of Dark Magic', 'Celeste',
           'Ghost Reaver, Longsword of Magic',
           'Celeste, Incarnation of the Corrupted', 'Glinting Glass Edge',
           'The Oculus, Token of Lost Worlds', 'Massacre',
           'Alpha, Oath of Zeal', 'Possessed Core', 'Foul Edge', 'Trickster',
           'Fusion Pummel', 'Stormfury Lantern', 'Apocalyptic Battlescythe',
           'Unholy Wand', 'Unending Tyranny', 'Ragnarok',
           'Rage, Legacy of the Lone Victor', 'Worldbreaker',
           'Exiled Mithril Longsword', 'Spectral Diamond Doomblade',
           'Vindictive Glass Edge', 'Heartseeker, Reaver of Souls',
           'Alpha, Reach of Ending Hope', 'Alpha', 'Betrayer',
           'Winterthorn, Defender of Shifting Worlds', "Gladiator's Glaive"],
          dtype=object)




```python
number_of_items = len(heros["Item ID"].unique())
number_of_items
```




    183




```python
avg_count = heros["Price"].mean()
avg_count

```




    3.050987179487176




```python
number_of_purchases = heros["Price"].sum()
number_of_purchases
```




    2379.77




```python
total_orders = heros["Purchase ID"].count()
total_orders
```




    780




```python
summary_purchase_df = pd.DataFrame({"Number of Unique Items":[number_of_items],
                                   "Avg Price": [avg_count],
                                   "Total Revenue": [number_of_purchases],
                                   "Total Orders": [total_orders]})
summary_purchase_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of Unique Items</th>
      <th>Avg Price</th>
      <th>Total Revenue</th>
      <th>Total Orders</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>183</td>
      <td>3.050987</td>
      <td>2379.77</td>
      <td>780</td>
    </tr>
  </tbody>
</table>
</div>



## Gender Demographics

* Percentage and Count of Male Players


* Percentage and Count of Female Players


* Percentage and Count of Other / Non-Disclosed





```python

```


```python
grouped_gender_df = heros.groupby(["Gender"])
print(grouped_gender_df)
grouped_gender_df.head()
grouped_gender_df.count()
```

    <pandas.core.groupby.groupby.DataFrameGroupBy object at 0x0000025A169E0400>
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>




```python
gender_df1 = heros.drop_duplicates("SN")
```


```python
male_count = gender_df1.loc[gender_df1["Gender"] == "Male"]
male_count
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Yalae81</td>
      <td>22</td>
      <td>Male</td>
      <td>81</td>
      <td>Dreamkiss</td>
      <td>3.61</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Itheria73</td>
      <td>36</td>
      <td>Male</td>
      <td>169</td>
      <td>Interrogator, Blood Blade of the Queen</td>
      <td>2.18</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Iskjaskst81</td>
      <td>20</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Undjask33</td>
      <td>22</td>
      <td>Male</td>
      <td>21</td>
      <td>Souleater</td>
      <td>1.10</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Inguron55</td>
      <td>23</td>
      <td>Male</td>
      <td>95</td>
      <td>Singed Onyx Warscythe</td>
      <td>4.74</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Haisrisuir60</td>
      <td>23</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Saelaephos52</td>
      <td>21</td>
      <td>Male</td>
      <td>116</td>
      <td>Renewed Skeletal Katana</td>
      <td>4.18</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Assjaskan73</td>
      <td>22</td>
      <td>Male</td>
      <td>4</td>
      <td>Bloodlord's Fetish</td>
      <td>1.70</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Saesrideu94</td>
      <td>35</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>4.86</td>
    </tr>
    <tr>
      <th>16</th>
      <td>16</td>
      <td>Lisirra25</td>
      <td>20</td>
      <td>Male</td>
      <td>40</td>
      <td>Second Chance</td>
      <td>2.52</td>
    </tr>
    <tr>
      <th>17</th>
      <td>17</td>
      <td>Zontibe81</td>
      <td>21</td>
      <td>Male</td>
      <td>161</td>
      <td>Devine</td>
      <td>1.76</td>
    </tr>
    <tr>
      <th>19</th>
      <td>19</td>
      <td>Chamalo71</td>
      <td>30</td>
      <td>Male</td>
      <td>89</td>
      <td>Blazefury, Protector of Delusions</td>
      <td>4.64</td>
    </tr>
    <tr>
      <th>20</th>
      <td>20</td>
      <td>Iathenudil29</td>
      <td>20</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
    </tr>
    <tr>
      <th>21</th>
      <td>21</td>
      <td>Phiarithdeu40</td>
      <td>20</td>
      <td>Male</td>
      <td>168</td>
      <td>Sun Strike, Jaws of Twisted Visions</td>
      <td>1.48</td>
    </tr>
    <tr>
      <th>23</th>
      <td>23</td>
      <td>Eyrian71</td>
      <td>40</td>
      <td>Male</td>
      <td>151</td>
      <td>Severance</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>24</th>
      <td>24</td>
      <td>Siala43</td>
      <td>30</td>
      <td>Male</td>
      <td>141</td>
      <td>Persuasion</td>
      <td>3.19</td>
    </tr>
    <tr>
      <th>25</th>
      <td>25</td>
      <td>Lisirra87</td>
      <td>29</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>Lirtossa84</td>
      <td>11</td>
      <td>Male</td>
      <td>71</td>
      <td>Demise</td>
      <td>1.61</td>
    </tr>
    <tr>
      <th>27</th>
      <td>27</td>
      <td>Eusri44</td>
      <td>7</td>
      <td>Male</td>
      <td>96</td>
      <td>Blood-Forged Skeletal Spine</td>
      <td>3.09</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>Aela59</td>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>4.32</td>
    </tr>
    <tr>
      <th>29</th>
      <td>29</td>
      <td>Tyida79</td>
      <td>24</td>
      <td>Male</td>
      <td>37</td>
      <td>Shadow Strike, Glory of Ending Hope</td>
      <td>3.16</td>
    </tr>
    <tr>
      <th>30</th>
      <td>30</td>
      <td>Idai61</td>
      <td>19</td>
      <td>Male</td>
      <td>140</td>
      <td>Striker</td>
      <td>2.94</td>
    </tr>
    <tr>
      <th>31</th>
      <td>31</td>
      <td>Farusrian86</td>
      <td>37</td>
      <td>Male</td>
      <td>179</td>
      <td>Wolf, Promise of the Moonwalker</td>
      <td>4.48</td>
    </tr>
    <tr>
      <th>32</th>
      <td>32</td>
      <td>Aeralria27</td>
      <td>10</td>
      <td>Male</td>
      <td>133</td>
      <td>Faith's Scimitar</td>
      <td>4.09</td>
    </tr>
    <tr>
      <th>33</th>
      <td>33</td>
      <td>Haillyrgue51</td>
      <td>7</td>
      <td>Male</td>
      <td>44</td>
      <td>Bonecarvin Battle Axe</td>
      <td>2.38</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>724</th>
      <td>724</td>
      <td>Lisassasta50</td>
      <td>25</td>
      <td>Male</td>
      <td>144</td>
      <td>Blood Infused Guardian</td>
      <td>1.94</td>
    </tr>
    <tr>
      <th>726</th>
      <td>726</td>
      <td>Iduelis31</td>
      <td>23</td>
      <td>Male</td>
      <td>21</td>
      <td>Souleater</td>
      <td>1.10</td>
    </tr>
    <tr>
      <th>728</th>
      <td>728</td>
      <td>Chanosiaya39</td>
      <td>44</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>1.97</td>
    </tr>
    <tr>
      <th>729</th>
      <td>729</td>
      <td>Assylla81</td>
      <td>20</td>
      <td>Male</td>
      <td>74</td>
      <td>Yearning Crusher</td>
      <td>4.18</td>
    </tr>
    <tr>
      <th>730</th>
      <td>730</td>
      <td>Aidaira26</td>
      <td>30</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
    </tr>
    <tr>
      <th>733</th>
      <td>733</td>
      <td>Chamiman85</td>
      <td>20</td>
      <td>Male</td>
      <td>66</td>
      <td>Victor Iron Spikes</td>
      <td>4.40</td>
    </tr>
    <tr>
      <th>736</th>
      <td>736</td>
      <td>Tyialisti80</td>
      <td>23</td>
      <td>Male</td>
      <td>58</td>
      <td>Freak's Bite, Favor of Holy Might</td>
      <td>4.14</td>
    </tr>
    <tr>
      <th>737</th>
      <td>737</td>
      <td>Marundi65</td>
      <td>22</td>
      <td>Male</td>
      <td>149</td>
      <td>Tranquility, Razor of Black Magic</td>
      <td>1.75</td>
    </tr>
    <tr>
      <th>738</th>
      <td>738</td>
      <td>Eusur90</td>
      <td>36</td>
      <td>Male</td>
      <td>121</td>
      <td>Massacre</td>
      <td>1.60</td>
    </tr>
    <tr>
      <th>739</th>
      <td>739</td>
      <td>Mindirranya33</td>
      <td>35</td>
      <td>Male</td>
      <td>61</td>
      <td>Ragnarok</td>
      <td>3.87</td>
    </tr>
    <tr>
      <th>741</th>
      <td>741</td>
      <td>Phiallylis33</td>
      <td>19</td>
      <td>Male</td>
      <td>145</td>
      <td>Fiery Glass Crusader</td>
      <td>4.58</td>
    </tr>
    <tr>
      <th>742</th>
      <td>742</td>
      <td>Isty55</td>
      <td>20</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>4.08</td>
    </tr>
    <tr>
      <th>743</th>
      <td>743</td>
      <td>Frichilsa31</td>
      <td>15</td>
      <td>Male</td>
      <td>110</td>
      <td>Suspension</td>
      <td>1.44</td>
    </tr>
    <tr>
      <th>745</th>
      <td>745</td>
      <td>Chanista95</td>
      <td>39</td>
      <td>Male</td>
      <td>37</td>
      <td>Shadow Strike, Glory of Ending Hope</td>
      <td>3.16</td>
    </tr>
    <tr>
      <th>746</th>
      <td>746</td>
      <td>Aellyria80</td>
      <td>23</td>
      <td>Male</td>
      <td>159</td>
      <td>Oathbreaker, Spellblade of Trials</td>
      <td>3.08</td>
    </tr>
    <tr>
      <th>748</th>
      <td>748</td>
      <td>Rastynusuir31</td>
      <td>20</td>
      <td>Male</td>
      <td>55</td>
      <td>Vindictive Glass Edge</td>
      <td>2.27</td>
    </tr>
    <tr>
      <th>750</th>
      <td>750</td>
      <td>Iljask75</td>
      <td>22</td>
      <td>Male</td>
      <td>167</td>
      <td>Malice, Legacy of the Queen</td>
      <td>3.61</td>
    </tr>
    <tr>
      <th>751</th>
      <td>751</td>
      <td>Lisjaskan36</td>
      <td>11</td>
      <td>Male</td>
      <td>180</td>
      <td>Stormcaller</td>
      <td>3.36</td>
    </tr>
    <tr>
      <th>752</th>
      <td>752</td>
      <td>Mindjasksya61</td>
      <td>17</td>
      <td>Male</td>
      <td>112</td>
      <td>Worldbreaker</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>753</th>
      <td>753</td>
      <td>Frichirranya75</td>
      <td>36</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
    </tr>
    <tr>
      <th>756</th>
      <td>756</td>
      <td>Ilast79</td>
      <td>20</td>
      <td>Male</td>
      <td>73</td>
      <td>Ritual Mace</td>
      <td>2.05</td>
    </tr>
    <tr>
      <th>757</th>
      <td>757</td>
      <td>Eratiel90</td>
      <td>18</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
    </tr>
    <tr>
      <th>761</th>
      <td>761</td>
      <td>Assim27</td>
      <td>45</td>
      <td>Male</td>
      <td>17</td>
      <td>Lazarus, Terror of the Earth</td>
      <td>1.70</td>
    </tr>
    <tr>
      <th>765</th>
      <td>765</td>
      <td>Irith83</td>
      <td>18</td>
      <td>Male</td>
      <td>130</td>
      <td>Alpha</td>
      <td>2.07</td>
    </tr>
    <tr>
      <th>769</th>
      <td>769</td>
      <td>Ilosian36</td>
      <td>15</td>
      <td>Male</td>
      <td>145</td>
      <td>Fiery Glass Crusader</td>
      <td>4.58</td>
    </tr>
    <tr>
      <th>771</th>
      <td>771</td>
      <td>Iskossasda43</td>
      <td>16</td>
      <td>Male</td>
      <td>25</td>
      <td>Hero Cane</td>
      <td>4.35</td>
    </tr>
    <tr>
      <th>773</th>
      <td>773</td>
      <td>Hala31</td>
      <td>21</td>
      <td>Male</td>
      <td>19</td>
      <td>Pursuit, Cudgel of Necromancy</td>
      <td>1.02</td>
    </tr>
    <tr>
      <th>774</th>
      <td>774</td>
      <td>Jiskjask80</td>
      <td>11</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
    </tr>
    <tr>
      <th>777</th>
      <td>777</td>
      <td>Yathecal72</td>
      <td>20</td>
      <td>Male</td>
      <td>67</td>
      <td>Celeste, Incarnation of the Corrupted</td>
      <td>3.46</td>
    </tr>
    <tr>
      <th>778</th>
      <td>778</td>
      <td>Sisur91</td>
      <td>7</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
    </tr>
  </tbody>
</table>
<p>484 rows × 7 columns</p>
</div>




```python
male_counts= male_count["Item ID"].count()
male_counts
```




    484




```python
female_count= gender_df1.loc[gender_df1["Gender"]=="Female"]

```


```python
female_counts = female_count["Item ID"].count()
female_counts
```




    81




```python
other_count = gender_df1.loc[gender_df1["Gender"]=="Other / Non-Disclosed"]

```


```python
other_counts = other_count["Item ID"].count()
other_counts
```




    11




```python
male_percent = (male_counts/576)*100
female_percent = (female_counts/576)*100
other_percent = (other_counts/576)*100
index = ["Male","Female", "Other Non-Disclosed"]

```


```python
Summary_Gender_Demo = pd.DataFrame({"Total Count": [male_counts, female_counts, other_counts],
                                   "Percentage of Players": [male_percent, female_percent, other_percent]},index=index)
Summary_Gender_Demo
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Count</th>
      <th>Percentage of Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>484</td>
      <td>84.027778</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>81</td>
      <td>14.062500</td>
    </tr>
    <tr>
      <th>Other Non-Disclosed</th>
      <td>11</td>
      <td>1.909722</td>
    </tr>
  </tbody>
</table>
</div>






## Purchasing Analysis (Gender)

* Run basic calculations to obtain purchase count, avg. purchase price, avg. purchase total per person etc. by gender




* Create a summary data frame to hold the results


* Optional: give the displayed data cleaner formatting


* Display the summary data frame


```python
grouped_gender_df = heros.groupby(["Gender"])
print(grouped_gender_df)
grouped_gender_df.head()
grouped_gender_df.count()
```

    <pandas.core.groupby.groupby.DataFrameGroupBy object at 0x0000025A169F2208>
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
      <td>113</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
      <td>652</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>




```python
item_count_M = heros.loc[heros["Gender"]== "Male"]

purchase_counts_M = item_count_M["Item ID"].count()
purchase_counts_M
```




    652




```python
item_count_F = heros.loc[heros["Gender"]== "Female"]
purchase_counts_F = item_count_F["Item ID"].count()
purchase_counts_F
```




    113




```python
item_count_O = heros.loc[heros["Gender"]== "Other / Non-Disclosed"]

purchase_count_O = item_count_O["Item ID"].count()
purchase_count_O
```




    15




```python
Male_Revenue = item_count_M["Price"].sum()
Male_Revenue
```




    1967.64




```python
Female_Revenue = item_count_F["Price"].sum()
Female_Revenue
```




    361.94




```python
Other_Revenue = item_count_O["Price"].sum()
Other_Revenue
```




    50.19




```python
avg_male_price = item_count_M["Price"].mean()
avg_male_price
```




    3.0178527607361953




```python
avg_female_price = item_count_F["Price"].mean()
avg_female_price
```




    3.203008849557519




```python
avg_other_price = item_count_O["Price"].mean()
avg_other_price
```




    3.3460000000000005




```python
avg_male_per_person = Male_Revenue/male_counts
avg_male_per_person
```




    4.065371900826446




```python
avg_female_per_person = Female_Revenue/female_counts
avg_female_per_person
```




    4.468395061728395




```python
avg_other_per_person = Other_Revenue/other_counts
avg_other_per_person
```




    4.5627272727272725




```python
summary_gender_df = pd.DataFrame({"Purchase Count": [purchase_counts_M, purchase_counts_F, purchase_count_O],
                                 "Avg Purchase Price":[avg_male_price,avg_female_price,avg_other_price],
                                 "Total Revenue": [Male_Revenue,Female_Revenue,Other_Revenue],
                                 "Avg per person": [avg_male_per_person,avg_female_per_person,avg_other_per_person]},index=index)
summary_gender_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Avg Purchase Price</th>
      <th>Total Revenue</th>
      <th>Avg per person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>652</td>
      <td>3.017853</td>
      <td>1967.64</td>
      <td>4.065372</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>113</td>
      <td>3.203009</td>
      <td>361.94</td>
      <td>4.468395</td>
    </tr>
    <tr>
      <th>Other Non-Disclosed</th>
      <td>15</td>
      <td>3.346000</td>
      <td>50.19</td>
      <td>4.562727</td>
    </tr>
  </tbody>
</table>
</div>



## Age Demographics

* Establish bins for ages


* Categorize the existing players using the age bins. Hint: use pd.cut()


* Calculate the numbers and percentages by age group


* Create a summary data frame to hold the results


* Optional: round the percentage column to two decimal points


* Display Age Demographics Table



```python
age_df = heros.drop_duplicates("SN")
age_df1 = age_df.dropna(how="any")
```


```python
age_bins =[0,9,14,19,24,29,34,39,100]
age_labels =["<10","10-14","15-19","20-24","25-29","30-34","35-39","40+"]
pd.cut(age_df1["Age"],age_bins, labels=age_labels)
age_df1["Age Bracket"]=pd.cut(age_df1["Age"],age_bins, labels=age_labels)
age_df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>Age Bracket</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Yalae81</td>
      <td>22</td>
      <td>Male</td>
      <td>81</td>
      <td>Dreamkiss</td>
      <td>3.61</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Itheria73</td>
      <td>36</td>
      <td>Male</td>
      <td>169</td>
      <td>Interrogator, Blood Blade of the Queen</td>
      <td>2.18</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Iskjaskst81</td>
      <td>20</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Undjask33</td>
      <td>22</td>
      <td>Male</td>
      <td>21</td>
      <td>Souleater</td>
      <td>1.10</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Chanosian48</td>
      <td>35</td>
      <td>Other / Non-Disclosed</td>
      <td>136</td>
      <td>Ghastly Adamantite Protector</td>
      <td>3.58</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Inguron55</td>
      <td>23</td>
      <td>Male</td>
      <td>95</td>
      <td>Singed Onyx Warscythe</td>
      <td>4.74</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Haisrisuir60</td>
      <td>23</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Saelaephos52</td>
      <td>21</td>
      <td>Male</td>
      <td>116</td>
      <td>Renewed Skeletal Katana</td>
      <td>4.18</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Assjaskan73</td>
      <td>22</td>
      <td>Male</td>
      <td>4</td>
      <td>Bloodlord's Fetish</td>
      <td>1.70</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Saesrideu94</td>
      <td>35</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>4.86</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>15</th>
      <td>15</td>
      <td>Lisassa64</td>
      <td>21</td>
      <td>Female</td>
      <td>98</td>
      <td>Deadline, Voice Of Subtlety</td>
      <td>2.89</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>16</th>
      <td>16</td>
      <td>Lisirra25</td>
      <td>20</td>
      <td>Male</td>
      <td>40</td>
      <td>Second Chance</td>
      <td>2.52</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>17</th>
      <td>17</td>
      <td>Zontibe81</td>
      <td>21</td>
      <td>Male</td>
      <td>161</td>
      <td>Devine</td>
      <td>1.76</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>18</th>
      <td>18</td>
      <td>Reunasu60</td>
      <td>22</td>
      <td>Female</td>
      <td>82</td>
      <td>Nirvana</td>
      <td>4.90</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>19</th>
      <td>19</td>
      <td>Chamalo71</td>
      <td>30</td>
      <td>Male</td>
      <td>89</td>
      <td>Blazefury, Protector of Delusions</td>
      <td>4.64</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>20</th>
      <td>20</td>
      <td>Iathenudil29</td>
      <td>20</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>21</th>
      <td>21</td>
      <td>Phiarithdeu40</td>
      <td>20</td>
      <td>Male</td>
      <td>168</td>
      <td>Sun Strike, Jaws of Twisted Visions</td>
      <td>1.48</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>22</th>
      <td>22</td>
      <td>Siarithria38</td>
      <td>38</td>
      <td>Other / Non-Disclosed</td>
      <td>24</td>
      <td>Warped Fetish</td>
      <td>3.81</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>23</th>
      <td>23</td>
      <td>Eyrian71</td>
      <td>40</td>
      <td>Male</td>
      <td>151</td>
      <td>Severance</td>
      <td>3.40</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>24</th>
      <td>24</td>
      <td>Siala43</td>
      <td>30</td>
      <td>Male</td>
      <td>141</td>
      <td>Persuasion</td>
      <td>3.19</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>25</th>
      <td>25</td>
      <td>Lisirra87</td>
      <td>29</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>Lirtossa84</td>
      <td>11</td>
      <td>Male</td>
      <td>71</td>
      <td>Demise</td>
      <td>1.61</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>27</th>
      <td>27</td>
      <td>Eusri44</td>
      <td>7</td>
      <td>Male</td>
      <td>96</td>
      <td>Blood-Forged Skeletal Spine</td>
      <td>3.09</td>
      <td>&lt;10</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>Aela59</td>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>4.32</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>29</th>
      <td>29</td>
      <td>Tyida79</td>
      <td>24</td>
      <td>Male</td>
      <td>37</td>
      <td>Shadow Strike, Glory of Ending Hope</td>
      <td>3.16</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>728</th>
      <td>728</td>
      <td>Chanosiaya39</td>
      <td>44</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>1.97</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>729</th>
      <td>729</td>
      <td>Assylla81</td>
      <td>20</td>
      <td>Male</td>
      <td>74</td>
      <td>Yearning Crusher</td>
      <td>4.18</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>730</th>
      <td>730</td>
      <td>Aidaira26</td>
      <td>30</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>731</th>
      <td>731</td>
      <td>Eudanu84</td>
      <td>22</td>
      <td>Female</td>
      <td>12</td>
      <td>Dawne</td>
      <td>1.02</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>733</th>
      <td>733</td>
      <td>Chamiman85</td>
      <td>20</td>
      <td>Male</td>
      <td>66</td>
      <td>Victor Iron Spikes</td>
      <td>4.40</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>736</th>
      <td>736</td>
      <td>Tyialisti80</td>
      <td>23</td>
      <td>Male</td>
      <td>58</td>
      <td>Freak's Bite, Favor of Holy Might</td>
      <td>4.14</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>737</th>
      <td>737</td>
      <td>Marundi65</td>
      <td>22</td>
      <td>Male</td>
      <td>149</td>
      <td>Tranquility, Razor of Black Magic</td>
      <td>1.75</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>738</th>
      <td>738</td>
      <td>Eusur90</td>
      <td>36</td>
      <td>Male</td>
      <td>121</td>
      <td>Massacre</td>
      <td>1.60</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>739</th>
      <td>739</td>
      <td>Mindirranya33</td>
      <td>35</td>
      <td>Male</td>
      <td>61</td>
      <td>Ragnarok</td>
      <td>3.87</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>741</th>
      <td>741</td>
      <td>Phiallylis33</td>
      <td>19</td>
      <td>Male</td>
      <td>145</td>
      <td>Fiery Glass Crusader</td>
      <td>4.58</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>742</th>
      <td>742</td>
      <td>Isty55</td>
      <td>20</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>4.08</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>743</th>
      <td>743</td>
      <td>Frichilsa31</td>
      <td>15</td>
      <td>Male</td>
      <td>110</td>
      <td>Suspension</td>
      <td>1.44</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>745</th>
      <td>745</td>
      <td>Chanista95</td>
      <td>39</td>
      <td>Male</td>
      <td>37</td>
      <td>Shadow Strike, Glory of Ending Hope</td>
      <td>3.16</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>746</th>
      <td>746</td>
      <td>Aellyria80</td>
      <td>23</td>
      <td>Male</td>
      <td>159</td>
      <td>Oathbreaker, Spellblade of Trials</td>
      <td>3.08</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>748</th>
      <td>748</td>
      <td>Rastynusuir31</td>
      <td>20</td>
      <td>Male</td>
      <td>55</td>
      <td>Vindictive Glass Edge</td>
      <td>2.27</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>750</th>
      <td>750</td>
      <td>Iljask75</td>
      <td>22</td>
      <td>Male</td>
      <td>167</td>
      <td>Malice, Legacy of the Queen</td>
      <td>3.61</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>751</th>
      <td>751</td>
      <td>Lisjaskan36</td>
      <td>11</td>
      <td>Male</td>
      <td>180</td>
      <td>Stormcaller</td>
      <td>3.36</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>752</th>
      <td>752</td>
      <td>Mindjasksya61</td>
      <td>17</td>
      <td>Male</td>
      <td>112</td>
      <td>Worldbreaker</td>
      <td>2.60</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>753</th>
      <td>753</td>
      <td>Frichirranya75</td>
      <td>36</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>756</th>
      <td>756</td>
      <td>Ilast79</td>
      <td>20</td>
      <td>Male</td>
      <td>73</td>
      <td>Ritual Mace</td>
      <td>2.05</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>757</th>
      <td>757</td>
      <td>Eratiel90</td>
      <td>18</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>761</th>
      <td>761</td>
      <td>Assim27</td>
      <td>45</td>
      <td>Male</td>
      <td>17</td>
      <td>Lazarus, Terror of the Earth</td>
      <td>1.70</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>765</th>
      <td>765</td>
      <td>Irith83</td>
      <td>18</td>
      <td>Male</td>
      <td>130</td>
      <td>Alpha</td>
      <td>2.07</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>769</th>
      <td>769</td>
      <td>Ilosian36</td>
      <td>15</td>
      <td>Male</td>
      <td>145</td>
      <td>Fiery Glass Crusader</td>
      <td>4.58</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>771</th>
      <td>771</td>
      <td>Iskossasda43</td>
      <td>16</td>
      <td>Male</td>
      <td>25</td>
      <td>Hero Cane</td>
      <td>4.35</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>773</th>
      <td>773</td>
      <td>Hala31</td>
      <td>21</td>
      <td>Male</td>
      <td>19</td>
      <td>Pursuit, Cudgel of Necromancy</td>
      <td>1.02</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>774</th>
      <td>774</td>
      <td>Jiskjask80</td>
      <td>11</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>775</th>
      <td>775</td>
      <td>Aethedru70</td>
      <td>21</td>
      <td>Female</td>
      <td>60</td>
      <td>Wolf</td>
      <td>3.54</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>777</th>
      <td>777</td>
      <td>Yathecal72</td>
      <td>20</td>
      <td>Male</td>
      <td>67</td>
      <td>Celeste, Incarnation of the Corrupted</td>
      <td>3.46</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>778</th>
      <td>778</td>
      <td>Sisur91</td>
      <td>7</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
      <td>&lt;10</td>
    </tr>
  </tbody>
</table>
<p>576 rows × 8 columns</p>
</div>




```python
age_df1["Age Bracket"].value_counts()
```




    20-24    258
    15-19    107
    25-29     77
    30-34     52
    35-39     31
    10-14     22
    <10       17
    40+       12
    Name: Age Bracket, dtype: int64




```python
percent_df =age_df1.loc[age_df1["Age Bracket"]=="<10"]
percent_df1 = percent_df["Item ID"].count()
u_10 = (percent_df1/576)*100
u_10
```




    2.951388888888889




```python
percent_df2 =age_df1.loc[age_df1["Age Bracket"]=="10-14"]
percent_df3 = percent_df2["Item ID"].count()
u_10_14= (percent_df3/576)*100
u_10_14
```




    3.8194444444444446




```python
percent_df4 =age_df1.loc[age_df1["Age Bracket"]=="15-19"]
percent_df5 = percent_df4["Item ID"].count()
u_15_19= (percent_df5/576)*100
u_15_19
```




    18.57638888888889




```python
percent_df6 =age_df1.loc[age_df1["Age Bracket"]=="20-24"]
percent_df7 = percent_df6["Item ID"].count()
u_20_24 = (percent_df7/576)*100
u_20_24
```




    44.79166666666667




```python
percent_df8 =age_df1.loc[age_df1["Age Bracket"]=="25-29"]
percent_df9 = percent_df8["Item ID"].count()
u_25_29 = (percent_df9/576)*100
u_25_29
```




    13.368055555555555




```python
percent_df10 =age_df1.loc[age_df1["Age Bracket"]=="30-34"]
percent_df11 = percent_df10["Item ID"].count()
u_30_34 = (percent_df11/576)*100
u_30_34
```




    9.027777777777777




```python
percent_df12 =age_df1.loc[age_df1["Age Bracket"]=="35-39"]
percent_df13 = percent_df12["Item ID"].count()
u_35_39 = (percent_df13/576)*100
u_35_39
```




    5.381944444444445




```python
percent_df14 =age_df1.loc[age_df1["Age Bracket"]=="40+"]
percent_df15 = percent_df14["Item ID"].count()
u_40 = (percent_df15/576)*100
u_40
```




    2.083333333333333




```python
Summary_Age_df = pd.DataFrame({"Total Count" : [percent_df1, percent_df3, percent_df5,percent_df7,percent_df9, percent_df11,percent_df13,percent_df15],
                  "Percentage of Players": [u_10, u_10_14, u_15_19, u_20_24, u_25_29, u_30_34, u_35_39, u_40]},index=age_labels)
Summary_Age_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Count</th>
      <th>Percentage of Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>17</td>
      <td>2.951389</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>22</td>
      <td>3.819444</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>107</td>
      <td>18.576389</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>258</td>
      <td>44.791667</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>77</td>
      <td>13.368056</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>52</td>
      <td>9.027778</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>31</td>
      <td>5.381944</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>12</td>
      <td>2.083333</td>
    </tr>
  </tbody>
</table>
</div>



## Purchasing Analysis (Age)

* Bin the purchase_data data frame by age


* Run basic calculations to obtain purchase count, avg. purchase price, avg. purchase total per person etc. in the table below


* Create a summary data frame to hold the results


* Optional: give the displayed data cleaner formatting


* Display the summary data frame


```python
purchase_df = pd.cut(heros["Age"],age_bins, labels=age_labels)
heros["Age Bracket"]=pd.cut(heros["Age"],age_bins, labels=age_labels)
heros
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>Age Bracket</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Yalae81</td>
      <td>22</td>
      <td>Male</td>
      <td>81</td>
      <td>Dreamkiss</td>
      <td>3.61</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Itheria73</td>
      <td>36</td>
      <td>Male</td>
      <td>169</td>
      <td>Interrogator, Blood Blade of the Queen</td>
      <td>2.18</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Iskjaskst81</td>
      <td>20</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Undjask33</td>
      <td>22</td>
      <td>Male</td>
      <td>21</td>
      <td>Souleater</td>
      <td>1.10</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Chanosian48</td>
      <td>35</td>
      <td>Other / Non-Disclosed</td>
      <td>136</td>
      <td>Ghastly Adamantite Protector</td>
      <td>3.58</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Inguron55</td>
      <td>23</td>
      <td>Male</td>
      <td>95</td>
      <td>Singed Onyx Warscythe</td>
      <td>4.74</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Haisrisuir60</td>
      <td>23</td>
      <td>Male</td>
      <td>162</td>
      <td>Abyssal Shard</td>
      <td>2.67</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Saelaephos52</td>
      <td>21</td>
      <td>Male</td>
      <td>116</td>
      <td>Renewed Skeletal Katana</td>
      <td>4.18</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Assjaskan73</td>
      <td>22</td>
      <td>Male</td>
      <td>4</td>
      <td>Bloodlord's Fetish</td>
      <td>1.70</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Saesrideu94</td>
      <td>35</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>4.86</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>15</th>
      <td>15</td>
      <td>Lisassa64</td>
      <td>21</td>
      <td>Female</td>
      <td>98</td>
      <td>Deadline, Voice Of Subtlety</td>
      <td>2.89</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>16</th>
      <td>16</td>
      <td>Lisirra25</td>
      <td>20</td>
      <td>Male</td>
      <td>40</td>
      <td>Second Chance</td>
      <td>2.52</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>17</th>
      <td>17</td>
      <td>Zontibe81</td>
      <td>21</td>
      <td>Male</td>
      <td>161</td>
      <td>Devine</td>
      <td>1.76</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>18</th>
      <td>18</td>
      <td>Reunasu60</td>
      <td>22</td>
      <td>Female</td>
      <td>82</td>
      <td>Nirvana</td>
      <td>4.90</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>19</th>
      <td>19</td>
      <td>Chamalo71</td>
      <td>30</td>
      <td>Male</td>
      <td>89</td>
      <td>Blazefury, Protector of Delusions</td>
      <td>4.64</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>20</th>
      <td>20</td>
      <td>Iathenudil29</td>
      <td>20</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>21</th>
      <td>21</td>
      <td>Phiarithdeu40</td>
      <td>20</td>
      <td>Male</td>
      <td>168</td>
      <td>Sun Strike, Jaws of Twisted Visions</td>
      <td>1.48</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>22</th>
      <td>22</td>
      <td>Siarithria38</td>
      <td>38</td>
      <td>Other / Non-Disclosed</td>
      <td>24</td>
      <td>Warped Fetish</td>
      <td>3.81</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>23</th>
      <td>23</td>
      <td>Eyrian71</td>
      <td>40</td>
      <td>Male</td>
      <td>151</td>
      <td>Severance</td>
      <td>3.40</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>24</th>
      <td>24</td>
      <td>Siala43</td>
      <td>30</td>
      <td>Male</td>
      <td>141</td>
      <td>Persuasion</td>
      <td>3.19</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>25</th>
      <td>25</td>
      <td>Lisirra87</td>
      <td>29</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>Lirtossa84</td>
      <td>11</td>
      <td>Male</td>
      <td>71</td>
      <td>Demise</td>
      <td>1.61</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>27</th>
      <td>27</td>
      <td>Eusri44</td>
      <td>7</td>
      <td>Male</td>
      <td>96</td>
      <td>Blood-Forged Skeletal Spine</td>
      <td>3.09</td>
      <td>&lt;10</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>Aela59</td>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>4.32</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>29</th>
      <td>29</td>
      <td>Tyida79</td>
      <td>24</td>
      <td>Male</td>
      <td>37</td>
      <td>Shadow Strike, Glory of Ending Hope</td>
      <td>3.16</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>750</th>
      <td>750</td>
      <td>Iljask75</td>
      <td>22</td>
      <td>Male</td>
      <td>167</td>
      <td>Malice, Legacy of the Queen</td>
      <td>3.61</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>751</th>
      <td>751</td>
      <td>Lisjaskan36</td>
      <td>11</td>
      <td>Male</td>
      <td>180</td>
      <td>Stormcaller</td>
      <td>3.36</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>752</th>
      <td>752</td>
      <td>Mindjasksya61</td>
      <td>17</td>
      <td>Male</td>
      <td>112</td>
      <td>Worldbreaker</td>
      <td>2.60</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>753</th>
      <td>753</td>
      <td>Frichirranya75</td>
      <td>36</td>
      <td>Male</td>
      <td>178</td>
      <td>Oathbreaker, Last Hope of the Breaking Storm</td>
      <td>4.23</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>754</th>
      <td>754</td>
      <td>Pheosurllorin41</td>
      <td>23</td>
      <td>Female</td>
      <td>79</td>
      <td>Alpha, Oath of Zeal</td>
      <td>4.05</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>755</th>
      <td>755</td>
      <td>Raesty92</td>
      <td>12</td>
      <td>Male</td>
      <td>76</td>
      <td>Haunted Bronzed Bludgeon</td>
      <td>3.15</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>756</th>
      <td>756</td>
      <td>Ilast79</td>
      <td>20</td>
      <td>Male</td>
      <td>73</td>
      <td>Ritual Mace</td>
      <td>2.05</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>757</th>
      <td>757</td>
      <td>Eratiel90</td>
      <td>18</td>
      <td>Male</td>
      <td>57</td>
      <td>Despair, Favor of Due Diligence</td>
      <td>4.60</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>758</th>
      <td>758</td>
      <td>Iral74</td>
      <td>21</td>
      <td>Male</td>
      <td>182</td>
      <td>Toothpick</td>
      <td>4.03</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>759</th>
      <td>759</td>
      <td>Tyaelorap29</td>
      <td>25</td>
      <td>Male</td>
      <td>72</td>
      <td>Winter's Bite</td>
      <td>3.77</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>760</th>
      <td>760</td>
      <td>Aithelis62</td>
      <td>21</td>
      <td>Male</td>
      <td>44</td>
      <td>Bonecarvin Battle Axe</td>
      <td>2.38</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>761</th>
      <td>761</td>
      <td>Assim27</td>
      <td>45</td>
      <td>Male</td>
      <td>17</td>
      <td>Lazarus, Terror of the Earth</td>
      <td>1.70</td>
      <td>40+</td>
    </tr>
    <tr>
      <th>762</th>
      <td>762</td>
      <td>Asur53</td>
      <td>26</td>
      <td>Male</td>
      <td>110</td>
      <td>Suspension</td>
      <td>1.44</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>763</th>
      <td>763</td>
      <td>Lassilsala30</td>
      <td>21</td>
      <td>Male</td>
      <td>85</td>
      <td>Malificent Bag</td>
      <td>1.75</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>764</th>
      <td>764</td>
      <td>Saedaiphos46</td>
      <td>18</td>
      <td>Male</td>
      <td>113</td>
      <td>Solitude's Reaver</td>
      <td>4.07</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>765</th>
      <td>765</td>
      <td>Irith83</td>
      <td>18</td>
      <td>Male</td>
      <td>130</td>
      <td>Alpha</td>
      <td>2.07</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>766</th>
      <td>766</td>
      <td>Aelastirin39</td>
      <td>23</td>
      <td>Male</td>
      <td>58</td>
      <td>Freak's Bite, Favor of Holy Might</td>
      <td>4.14</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>767</th>
      <td>767</td>
      <td>Ilmol66</td>
      <td>8</td>
      <td>Female</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
      <td>&lt;10</td>
    </tr>
    <tr>
      <th>768</th>
      <td>768</td>
      <td>Assassasta79</td>
      <td>38</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
      <td>35-39</td>
    </tr>
    <tr>
      <th>769</th>
      <td>769</td>
      <td>Ilosian36</td>
      <td>15</td>
      <td>Male</td>
      <td>145</td>
      <td>Fiery Glass Crusader</td>
      <td>4.58</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>770</th>
      <td>770</td>
      <td>Lirtosia63</td>
      <td>34</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>1.02</td>
      <td>30-34</td>
    </tr>
    <tr>
      <th>771</th>
      <td>771</td>
      <td>Iskossasda43</td>
      <td>16</td>
      <td>Male</td>
      <td>25</td>
      <td>Hero Cane</td>
      <td>4.35</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>772</th>
      <td>772</td>
      <td>Asur53</td>
      <td>26</td>
      <td>Male</td>
      <td>136</td>
      <td>Ghastly Adamantite Protector</td>
      <td>3.58</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>773</th>
      <td>773</td>
      <td>Hala31</td>
      <td>21</td>
      <td>Male</td>
      <td>19</td>
      <td>Pursuit, Cudgel of Necromancy</td>
      <td>1.02</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>774</th>
      <td>774</td>
      <td>Jiskjask80</td>
      <td>11</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
      <td>10-14</td>
    </tr>
    <tr>
      <th>775</th>
      <td>775</td>
      <td>Aethedru70</td>
      <td>21</td>
      <td>Female</td>
      <td>60</td>
      <td>Wolf</td>
      <td>3.54</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>776</th>
      <td>776</td>
      <td>Iral74</td>
      <td>21</td>
      <td>Male</td>
      <td>164</td>
      <td>Exiled Doomblade</td>
      <td>1.63</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>777</th>
      <td>777</td>
      <td>Yathecal72</td>
      <td>20</td>
      <td>Male</td>
      <td>67</td>
      <td>Celeste, Incarnation of the Corrupted</td>
      <td>3.46</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>778</th>
      <td>778</td>
      <td>Sisur91</td>
      <td>7</td>
      <td>Male</td>
      <td>101</td>
      <td>Final Critic</td>
      <td>4.19</td>
      <td>&lt;10</td>
    </tr>
    <tr>
      <th>779</th>
      <td>779</td>
      <td>Ennrian78</td>
      <td>24</td>
      <td>Male</td>
      <td>50</td>
      <td>Dawn</td>
      <td>4.60</td>
      <td>20-24</td>
    </tr>
  </tbody>
</table>
<p>780 rows × 8 columns</p>
</div>



## Top Spenders

* Run basic calculations to obtain the results in the table below


* Create a summary data frame to hold the results


* Sort the total purchase value column in descending order


* Optional: give the displayed data cleaner formatting


* Display a preview of the summary data frame




```python
spenders= heros.loc[heros["Age Bracket"]=="<10"]
spenders_u_10 =spenders["Price"].sum()
spenders_u_10
```




    77.13




```python
grouped_spenders_heros = heros.groupby("Age Bracket")

print(grouped_spenders_heros)
count = grouped_spenders_heros["Item ID"].count()

```

    <pandas.core.groupby.groupby.DataFrameGroupBy object at 0x0000025A16A506D8>
    


```python
total_rev = grouped_spenders_heros["Price"].sum()

```


```python
avg_price = grouped_spenders_heros["Price"].mean()
```


```python
merged = pd.concat([count,total_rev,], axis=1)
merged
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item ID</th>
      <th>Price</th>
    </tr>
    <tr>
      <th>Age Bracket</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>23</td>
      <td>77.13</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>28</td>
      <td>82.78</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>136</td>
      <td>412.89</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>365</td>
      <td>1114.06</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>101</td>
      <td>293.00</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>73</td>
      <td>214.00</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>41</td>
      <td>147.67</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>13</td>
      <td>38.24</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged_df = merged.rename(index=str, columns={"Price":"Total Revenue"})
merged_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item ID</th>
      <th>Total Revenue</th>
    </tr>
    <tr>
      <th>Age Bracket</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>23</td>
      <td>77.13</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>28</td>
      <td>82.78</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>136</td>
      <td>412.89</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>365</td>
      <td>1114.06</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>101</td>
      <td>293.00</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>73</td>
      <td>214.00</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>41</td>
      <td>147.67</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>13</td>
      <td>38.24</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged_df1= pd.concat([merged_df, avg_price],axis=1)

```


```python

```


```python
heros_pp = heros.groupby(["SN", "Age Bracket"]).sum().groupby(["Age Bracket"]).mean()


```


```python
heros_pp.drop(["Item ID"],axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>Age</th>
      <th>Price</th>
    </tr>
    <tr>
      <th>Age Bracket</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>588.764706</td>
      <td>10.647059</td>
      <td>4.537059</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>459.727273</td>
      <td>14.500000</td>
      <td>3.762727</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>512.700935</td>
      <td>21.345794</td>
      <td>3.858785</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>540.980620</td>
      <td>30.895349</td>
      <td>4.318062</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>533.402597</td>
      <td>34.103896</td>
      <td>3.805195</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>504.884615</td>
      <td>44.057692</td>
      <td>4.115385</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>535.354839</td>
      <td>48.548387</td>
      <td>4.763548</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>444.416667</td>
      <td>45.000000</td>
      <td>3.186667</td>
    </tr>
  </tbody>
</table>
</div>




```python
heros_1 =heros_pp.rename(index=str, columns={"Price": "Avg Per Person"})
```


```python
heros_1.drop(["Item ID"],axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>Age</th>
      <th>Avg Per Person</th>
    </tr>
    <tr>
      <th>Age Bracket</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>588.764706</td>
      <td>10.647059</td>
      <td>4.537059</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>459.727273</td>
      <td>14.500000</td>
      <td>3.762727</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>512.700935</td>
      <td>21.345794</td>
      <td>3.858785</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>540.980620</td>
      <td>30.895349</td>
      <td>4.318062</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>533.402597</td>
      <td>34.103896</td>
      <td>3.805195</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>504.884615</td>
      <td>44.057692</td>
      <td>4.115385</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>535.354839</td>
      <td>48.548387</td>
      <td>4.763548</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>444.416667</td>
      <td>45.000000</td>
      <td>3.186667</td>
    </tr>
  </tbody>
</table>
</div>




```python
summary_age_purchase = pd.merge(merged_df1,heros_1, on="Age Bracket")
summary_age_purchase
summary_age_purchase.drop(["Item ID_y"], axis=1)
summary_age_purchase.rename(index=str,columns={"Price": "Avg Price", "Item ID_x": "Number of Users"})

summary_age_purchase_1 = summary_age_purchase.drop(["Item ID_y", "Purchase ID", "Age"], axis=1)
summary_age_purchase_1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Item ID_x</th>
      <th>Total Revenue</th>
      <th>Price</th>
      <th>Avg Per Person</th>
    </tr>
    <tr>
      <th>Age Bracket</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>23</td>
      <td>77.13</td>
      <td>3.353478</td>
      <td>4.537059</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>28</td>
      <td>82.78</td>
      <td>2.956429</td>
      <td>3.762727</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>136</td>
      <td>412.89</td>
      <td>3.035956</td>
      <td>3.858785</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>365</td>
      <td>1114.06</td>
      <td>3.052219</td>
      <td>4.318062</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>101</td>
      <td>293.00</td>
      <td>2.900990</td>
      <td>3.805195</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>73</td>
      <td>214.00</td>
      <td>2.931507</td>
      <td>4.115385</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>41</td>
      <td>147.67</td>
      <td>3.601707</td>
      <td>4.763548</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>13</td>
      <td>38.24</td>
      <td>2.941538</td>
      <td>3.186667</td>
    </tr>
  </tbody>
</table>
</div>




```python

most_pop1 = heros.groupby(["SN"]).sum()["Price"]
most_pop2 = heros.groupby(["SN"]).count()["Price"]
most_pop3 = heros.groupby(["SN"]).mean()["Price"]


Summary_Pop_Df = pd.DataFrame({"Purchase Count": most_pop2,
                              "Avg Price": most_pop3,
                              "Total Spent": most_pop1})

Summary_Pop_Df = Summary_Pop_Df.sort_values(["Total Spent"], ascending=False)
Summary_Pop_Df.head()
# total
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase Count</th>
      <th>Avg Price</th>
      <th>Total Spent</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Lisosia93</th>
      <td>5</td>
      <td>3.792000</td>
      <td>18.96</td>
    </tr>
    <tr>
      <th>Idastidru52</th>
      <td>4</td>
      <td>3.862500</td>
      <td>15.45</td>
    </tr>
    <tr>
      <th>Chamjask73</th>
      <td>3</td>
      <td>4.610000</td>
      <td>13.83</td>
    </tr>
    <tr>
      <th>Iral74</th>
      <td>4</td>
      <td>3.405000</td>
      <td>13.62</td>
    </tr>
    <tr>
      <th>Iskadarya95</th>
      <td>3</td>
      <td>4.366667</td>
      <td>13.10</td>
    </tr>
  </tbody>
</table>
</div>



## Most Popular Items


```python
* Retrieve the Item ID, Item Name, and Item Price columns


* Group by Item ID and Item Name. Perform calculations to obtain purchase count, item price, and total purchase value


* Create a summary data frame to hold the results


* Sort the purchase count column in descending order


* Optional: give the displayed data cleaner formatting


* Display a preview of the summary data frame


```


      File "<ipython-input-62-d23d94703aa5>", line 1
        * Retrieve the Item ID, Item Name, and Item Price columns
                     ^
    SyntaxError: invalid syntax
    



```python
items= heros.groupby(["Item Name", "Item ID"]).count()["Price"]
items2 = heros.groupby(["Item Name", "Item ID"]).sum()["Price"]
items3 = heros.groupby(["Item Name", "Item ID"]).mean()["Price"]

summary_item_df = pd.DataFrame({"Purchase Count": items,
                   "Item Price": items3,
                   "Total Purchase Value": items2})
summary_item_df = summary_item_df.sort_values("Purchase Count", ascending=False)
summary_item_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Item Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item Name</th>
      <th>Item ID</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Oathbreaker, Last Hope of the Breaking Storm</th>
      <th>178</th>
      <td>12</td>
      <td>4.23</td>
      <td>50.76</td>
    </tr>
    <tr>
      <th>Extraction, Quickblade Of Trembling Hands</th>
      <th>108</th>
      <td>9</td>
      <td>3.53</td>
      <td>31.77</td>
    </tr>
    <tr>
      <th>Nirvana</th>
      <th>82</th>
      <td>9</td>
      <td>4.90</td>
      <td>44.10</td>
    </tr>
    <tr>
      <th>Fiery Glass Crusader</th>
      <th>145</th>
      <td>9</td>
      <td>4.58</td>
      <td>41.22</td>
    </tr>
    <tr>
      <th>Pursuit, Cudgel of Necromancy</th>
      <th>19</th>
      <td>8</td>
      <td>1.02</td>
      <td>8.16</td>
    </tr>
  </tbody>
</table>
</div>



## Most Profitable Items


```python
items= heros.groupby(["Item Name", "Item ID"]).count()["Price"]
items2 = heros.groupby(["Item Name", "Item ID"]).sum()["Price"]
items3 = heros.groupby(["Item Name", "Item ID"]).mean()["Price"]

summary_item_df = pd.DataFrame({"Purchase Count": items,
                   "Item Price": items3,
                   "Total Purchase Value": items2})
summary_item_df = summary_item_df.sort_values("Total Purchase Value", ascending=False)
summary_item_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Item Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item Name</th>
      <th>Item ID</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Oathbreaker, Last Hope of the Breaking Storm</th>
      <th>178</th>
      <td>12</td>
      <td>4.23</td>
      <td>50.76</td>
    </tr>
    <tr>
      <th>Nirvana</th>
      <th>82</th>
      <td>9</td>
      <td>4.90</td>
      <td>44.10</td>
    </tr>
    <tr>
      <th>Fiery Glass Crusader</th>
      <th>145</th>
      <td>9</td>
      <td>4.58</td>
      <td>41.22</td>
    </tr>
    <tr>
      <th>Final Critic</th>
      <th>92</th>
      <td>8</td>
      <td>4.88</td>
      <td>39.04</td>
    </tr>
    <tr>
      <th>Singed Scalpel</th>
      <th>103</th>
      <td>8</td>
      <td>4.35</td>
      <td>34.80</td>
    </tr>
  </tbody>
</table>
</div>



* Sort the above table by total purchase value in descending order


* Optional: give the displayed data cleaner formatting


* Display a preview of the data frame




```python

```
