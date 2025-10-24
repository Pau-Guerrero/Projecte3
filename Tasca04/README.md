# T04: Serveis de directori - LDAP

## Breu resum
Innovatech té problemes de gestió d'usuaris i accessos perquè cada servei i cada ordinador utilitza comptes locals o bases de dades separades. Això provoca:
- **Ineficiència operativa:** Cada nou usuari o baixa s’ha de replicar en tots els sistemes.
- **Risc de seguretat:** Els usuaris reutilitzen contrasenyes entre serveis.
- **Manca d’escalabilitat:** Afegir nous serveis és complicat.

## Solució proposada
S’ha decidit implementar **OpenLDAP** per centralitzar l’autenticació i la gestió d’usuaris. OpenLDAP és:
- De codi obert.
- Robúst.
- Compatible amb GNU/Linux, que és el sistema que utilitzen tots els ordinadors de l’empresa.

## Objectius de l’exercici
1. **Instal·lar OpenLDAP en un servidor Linux.**
2. **Configurar el domini base** del directori.
3. **Crear la jerarquia d’unitats organitzatives (OUs)** per organitzar els usuaris i grups.
4. **Afegir usuaris i grups** que després serviran per donar accés a serveis de xarxa.
5. **Configurar un client Linux** perquè s’autentiqui utilitzant el directori LDAP.

## Material de suport
Al Moodle de l’assignatura tens disponible:
- UD04.AA1 Serveis de Directori
- UD04.AA2 Instal·lació OpenLDAP
- UD04.AA3 Configuració del directori
- UD04.AA5 Afegir client al directori

## Consells per fer l’exercici
- Seguiu el plec de condicions tècniques proporcionat.
- Comproveu que els usuaris creats al servidor LDAP poden iniciar sessió des del client.
- Mantingueu una jerarquia clara d’unitats organitzatives i grups.
- Documenteu cada pas per a futures referències i per facilitar la correcció.

