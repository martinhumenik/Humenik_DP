
# Využitie hlbokého učenia pre analýzu ionosférických dát

## Martin Humeník - Diplomová práca

### Hospodárska informatika, KKUI, FEI TUKE 2025

### Datasety
Príprava dát:
- Načítanie dát o amplitúde z .zip súborov - súbor [**data_load.ipynb**](data_load.ipynb), link na stiahnutie datasetu - 
- Predspracovanie a odvodenie nových atribútov pri amplitúde, integrácia a predspracovanie zemetrasení v .csv súboroch - [**data_preparation.ipynb**](data_preparation.ipynb). Zjednotený dataset zemetrasení - [**earthquakes.csv**](earthquakes.csv). Zemetrasenia je možné stiahnúť na [LINK](https://www.emsc-csem.org/Earthquake_information/#) a je ich potrebné nahrať do súboru earthquakes.
- Výpočet vzdialenosti medzi vysielačmi a prijímačom, selekcia zemetrasení na modelovnaie - [**distance_calculation.ipynb**](distance_calculation.ipynb), datasety s vyselektovanými zemetraseniami - [**eq_biggest_influence_per_hour.csv**](eq_biggest_influence_per_hour.csv), [**eq_influence_on_path.csv**](eq_influence_on_path.csv).
- Príprava amplitúdy na modelovanie, vytvorenie datasetov s pozitívnymi a negatívnymi príkladmi - [**model_data_preproccesing.ipynb**](model_data_preproccesing.ipynb), liny na stiahnutie datasetov - [amp_windows_positive_6h.csv](https://mega.nz/file/0b9iyLLD#GPD6LEBYLI4Jh1YO0Nmss6-BJfCqwdxlc2LtMkog1TE), [amp_windows_negative_6h.csv](https://mega.nz/file/Ea812ZBJ#xa4tI18XmHH_KGsL-1JFRFmyPIAbmkZJT3hdwwyEEpk), [amp_windows_positive_3h_prediction.csv](https://mega.nz/file/1a9kAa4K#BT7E-2LE9xapr7jXMzI7LDkQnAgVo02WhBk4A4RTkjs), [amp_windows_negative_3h_prediction.csv](https://mega.nz/file/sCESCIra#hxH-LqYqU5TSZW-ewqvkgacoAOxJ4myWSS6p37sdJZM)

Vizualizácia dát:
- Vizualizácia vysielačov, prijímača a zemetrasení v rámci Európy. Distribúcia hodnôt atribútu magnitúda pri zemetraseniach. Vykreslenie amplitúdy - [**visualisation.ipynb**](visualisation.ipynb).

### Modelovanie
Trénovanie, validácia a testovanie modelov, uloženie vytvorených modelov.

#### Frekvenčná doména:
- Modelovanie na fourierovej amplitúde vytvorenej z 6 hodinového okna s dlhšími periódami (od 6 sekúnd do 180 minút) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_6h.ipynb**](NN_freq_domain_6h.ipynb).

- Modelovanie na fourierovej amplitúde vytvorenej z 6 hodinového okna s kratšími periódami (od 1 sekundy do 6 sekúnd) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_6h_short_per.ipynb**](NN_freq_domain_6h_short_per.ipynb).

- Modelovanie na fourierovej amplitúde vytvorenej z 3 hodinového okna s dlhšími periódami (od 6 sekúnd do 180 minút) pomocou konvolučnej neurónovej siete, doprednej neurónovej siete - súbor [**NN_freq_domain_3h.ipynb**](NN_freq_domain_3h.ipynb).

#### Časová a frekvenčná doména (jednoduchšie modely):
Modelovanie na 6 hodinovom okne aplitúdy a na fourierovej amplitúde vytvorenej z 6 hodinového okna pomocou metód logistická regresia, náhodné lesy, K-najbližších susedov, stroje s podpornými vektormi - súbor [**models_all_domain.ipynb**](models_all_domain.ipynb).

### Modely:
#### Časová doména:
- Logistická regresia - súbor [**lr_cd.pkl**](lr_cd.pkl).
- K-nn - link na stiahnutie [knn_cd.pkl](https://mega.nz/file/pXFTkajT#uFdr2d29VlbsXg2sn2Dps7aYtP-aajUYujqTvhQ_iw4).
- RF - súbor [**rf_cd.pkl**](rf_cd.pkl).
- SVM - súbor [**svm_cd.pkl**](svm_cd.pkl).

#### Frekvenčná doména:
Fourierová amplitúda vytvorená zo 6 hodinové okna s dlhými periódami
- Logistická regresia - súbor [**lr_fd.pkl**](lr_fd.pkl).
- K-nn - súbor [**knn_fd.pkl**](knn_fd.pkl).
- RF - súbor [**rf_fd.pkl**](rf_fd.pkl).
- SVM - súbor [**svm_fd.pkl**](svm_fd.pkl).

- Konvolučná nerónová sieť - súbor [**nn_conv_6h.pkl**](nn_conv_6h.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_6h.pkl**](nn_mlp_6h.pkl).

Fourierová amplitúda vytvorená zo 6 hodinové okna s krátkymi periódami
- Konvolučná nerónová sieť - súbor [**nn_conv_6h_short_per.pkl**](nn_conv_6h_short_per.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_6h_short_per.pkl**](nn_mlp_6h_short_per.pkl).
- SVM - súbor [**svm_fd_6h_short_per.pkl**](svm_fd_6h_short_per.pkl).

Fourierová amplitúda vytvorená z 3 hodinové okna s dlhými periódami
- Konvolučná nerónová sieť - súbor [**nn_conv_3h.pkl**](nn_conv_3h.pkl).
- Dopredná neurónová sieť - súbor [**nn_mlp_3h.pkl**](nn_mlp_3h.pkl).
