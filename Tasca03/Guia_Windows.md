# T03: Gestió flexible de discos (LVM i Espais d’emmagatzematge)

**Autors:** Xavi López i Pau Guerrero

**Part Windows:** Espais d’Emmagatzematge (Storage Spaces)

Per a aquesta pràctica s’utilitza **Windows 11** per demostrar les configuracions possibles mitjançant els Espais d’Emmagatzematge (Storage Spaces).

---

## Requisits de la Implementació i Demostració

- **Configuració inicial:**  
  Creació d’un **pool d’emmagatzematge** amb tres discos virtuals de 10 GB (simulats).

- **Estudi de configuracions:**  
  - **Resiliència de Mirall (Mirroring):** utilitzant dos discos per comprovar l’alta disponibilitat.  
  - **Mirall triple:** creació d’un espai amb tres discos per mostrar la major seguretat respecte al mirroring doble.  
  - **Resiliència de Paritat (Parity):** demostració de la seva eficiència d’espai respecte al mirall.

- **Demostració de la gestió:**  
  Visualització de l’estat dels discos i del pool des de la consola de Windows.

---

## 1. Administrar discos

Es gestionen els tres discos simulats de 10 GB (1, 2 i 3) prèviament creats.  
S’utilitza el tipus de partició **MBR (Registre d’arrencada mestre)** per a cadascun dels discos.

! [](img/img_Windows)
---

## 2. Resiliència de mirall

En aquesta configuració s’utilitzen **dos discos** per crear un espai d’emmagatzematge amb resiliència de mirall doble.  
Aquesta configuració permet mantenir una **alta disponibilitat de les dades**, ja que es creen còpies redundants que garanteixen la seva integritat en cas de fallada d’un dels discos.

**Detalls de configuració:**

- Nom de l’espai: Espai d’emmagatzematge  
- Sistema de fitxers: NTFS  
- Capacitat màxima: 10 GB  
- Capacitat total del pool: 18,7 GB

---

## 3. Resiliència de paritat

Es crea un nou espai d’emmagatzematge amb **resiliència de paritat**, afegint-hi una unitat addicional de 10 GB per millorar la distribució de les dades dins del grup.  

Aquesta configuració és més **eficient en l’ús de l’espai**, ja que només una part es destina a la informació de paritat, i la resta a dades útils.

---

## 4. Resiliència de mirall triple

Un cop demostrada la configuració anterior, es desfà l’espai de mirall i se’n crea un de nou amb **resiliència de mirall triple**, utilitzant **tres discos de 10 GB**.  

Aquesta opció ofereix un **nivell superior de protecció**, ja que permet resistir la fallada simultània de fins a dos discos sense pèrdua d’informació.

**Avantatges respecte al mirroring doble:**

- Major nivell de protecció.  
- Possibilitat de fallada de dos discos sense pèrdua de dades.  
- Més seguretat per a entorns crítics.

