
# Využitie hlbokého učenia pre analýzu ionosférických dát

## Martin Humeník - Diplomová práca

### Hospodárska informatika, KKUI, FEI TUKE 2025

### Datasety
Príprava dát:
- Načítanie dát o amplitúde z .zip súborov - súbor [**data_load.ipynb**](data_load.ipynb), link na stiahnutie .zip súborov - [1to15Oct_DHO_JXN_GVT.zip](https://mega.nz/file/MPdiRIoB#OKKyhhqDyEPlf8Lzj0ytmdcTgGwB5dz73YdoN6jf3xA), [16to31Oct_DHO_JXN_GVT.zip](https://mega.nz/file/UT9mgCaA#eCN4CylcQW4B0QaJsF3NBCsJY5_sqoknjl6vv-es5CA), [1to15Nov_DHO_JXN_GVT.zip](https://mega.nz/file/xOcCVLqZ#p3mG-esxmwHVfNgyd5HsQec5gkbwM5ywT5Q4qSOE6qY), [ICV.zip](https://mega.nz/file/taUj2b4Y#_VznXRFbyeQV0FdjZBCGBKlrnAasukiK8WJ5q1FSqgo)
- Predspracovanie a odvodenie nových atribútov pri amplitúde, integrácia a predspracovanie zemetrasení v .csv súboroch - [**data_preparation.ipynb**](data_preparation.ipynb). Zjednotený dataset zemetrasení - [**earthquakes.csv**](earthquakes.csv). Zemetrasenia je možné stiahnúť na [LINK](https://www.emsc-csem.org/Earthquake_information/#) a je ich potrebné nahrať do súboru earthquakes.
- Výpočet vzdialenosti medzi vysielačmi a prijímačom, selekcia zemetrasení na modelovnaie - [**distance_calculation.ipynb**](distance_calculation.ipynb), datasety s vyselektovanými zemetraseniami - [**eq_biggest_influence_per_hour.csv**](eq_biggest_influence_per_hour.csv), [**eq_influence_on_path.csv**](eq_influence_on_path.csv).
- Príprava amplitúdy na modelovanie, vytvorenie datasetov s pozitívnymi a negatívnymi príkladmi - [**model_data_preproccesing.ipynb**](model_data_preproccesing.ipynb), liny na stiahnutie datasetov - [amp_windows_positive_6h.csv](https://mega.nz/file/0b9iyLLD#GPD6LEBYLI4Jh1YO0Nmss6-BJfCqwdxlc2LtMkog1TE), [amp_windows_negative_6h.csv](https://mega.nz/file/Ea812ZBJ#xa4tI18XmHH_KGsL-1JFRFmyPIAbmkZJT3hdwwyEEpk), [amp_windows_positive_3h_prediction.csv](https://mega.nz/file/1a9kAa4K#BT7E-2LE9xapr7jXMzI7LDkQnAgVo02WhBk4A4RTkjs), [amp_windows_negative_3h_prediction.csv](https://mega.nz/file/sCESCIra#hxH-LqYqU5TSZW-ewqvkgacoAOxJ4myWSS6p37sdJZM)

Vizualizácia dát:
- Vizualizácia vysielačov, prijímača a zemetrasení v rámci Európy. Distribúcia hodnôt atribútu magnitúda pri zemetraseniach. Vykreslenie amplitúdy - [**visualisation.ipynb**](visualisation.ipynb).

### Modelovanie
Trénovanie, validácia a testovanie modelov, uloženie vytvorených modelov.

#### Frekvenčná doména:
- Modelovanie na fourierovej amplitúde vytvorenej z 6 hodinového okna s dlhšími periódami (od 6 sekúnd do 180 minút) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_6h.ipynb**](ML/NN_freq_domain_6h.ipynb).

- Modelovanie na fourierovej amplitúde vytvorenej z 6 hodinového okna s kratšími periódami (od 1 sekundy do 6 sekúnd) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_6h_short_per.ipynb**](ML/NN_freq_domain_6h_short_per.ipynb).

- Modelovanie na fourierovej amplitúde vytvorenej z 3 hodinového okna s dlhšími periódami (od 6 sekúnd do 180 minút) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_3h.ipynb**](ML/NN_freq_domain_3h.ipynb).

#### Časová a frekvenčná doména (jednoduchšie modely):
Modelovanie na 6 hodinovom okne aplitúdy a na fourierovej amplitúde vytvorenej z 6 hodinového okna pomocou metód logistická regresia, náhodné lesy, K-najbližších susedov, stroje s podpornými vektormi - súbor [**models_time_domain.ipynb**](ML/models_time_domain.ipynb).

### Postupnosť spúšťania jednotlivých súborov
- data_load.ipynb - načítanie dát z .zip súborov
- data_preparation.ipynb - odvodenie nových atribútov pri amplitúde, príprava datestu o zemetraseniach
- distance_calculation.ipynb - selekcia zemetrasení
- model_data_preproccesing.ipynb - príprava amplitúdy na modelovanie
- následuje samotné modelovanie - NN_freq_domain_6h.ipynb, NN_freq_domain_6h_short_per.ipynb, NN_freq_domain_3h.ipynb, models_all_domain.ipynb

### Modely:
#### Časová doména:
- Logistická regresia - súbor [**lr_cd.pkl**](ML/models/lr_cd.pkl).
- K-nn - link na stiahnutie [knn_cd.pkl](https://mega.nz/file/pXFTkajT#uFdr2d29VlbsXg2sn2Dps7aYtP-aajUYujqTvhQ_iw4).
- RF - súbor [**rf_cd.pkl**](ML/models/rf_cd.pkl).
- SVM - súbor [**svm_cd.pkl**](ML/models/svm_cd.pkl).

#### Frekvenčná doména:
Fourierová amplitúda vytvorená zo 6 hodinové okna s dlhými periódami
- Logistická regresia - súbor [**lr_fd.pkl**](ML/models/lr_fd.pkl).
- K-nn - súbor [**knn_fd.pkl**](ML/models/knn_fd.pkl).
- RF - súbor [**rf_fd.pkl**](ML/models/rf_fd.pkl).
- SVM - súbor [**svm_fd.pkl**](ML/models/svm_fd.pkl).

- Konvolučná nerónová sieť - súbor [**nn_conv_6h.pkl**](ML/models/nn_conv_6h.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_6h.pkl**](ML/models/nn_mlp_6h.pkl).

Fourierová amplitúda vytvorená zo 6 hodinové okna s krátkymi periódami
- Konvolučná nerónová sieť - súbor [**nn_conv_6h_short_per.pkl**](ML/models/nn_conv_6h_short_per.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_6h_short_per.pkl**](ML/models/nn_mlp_6h_short_per.pkl).
- SVM - súbor [**svm_fd_6h_short_per.pkl**](ML/models/svm_fd_6h_short_per.pkl).

Fourierová amplitúda vytvorená z 3 hodinové okna s dlhými periódami
- Konvolučná nerónová sieť - súbor [**nn_conv_3h.pkl**](ML/models/nn_conv_3h.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_3h.pkl**](ML/models/nn_mlp_3h.pkl).
