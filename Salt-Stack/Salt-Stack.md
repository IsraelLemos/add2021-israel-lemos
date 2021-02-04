## Salt Stack

### 3.4 Comprobamos conectividad
 - Desde el Máster comprobamos:

 - Conectividad hacia los Minions:
    - salt '*' test.ping
    - minionXXg:
    - True

![3.4.1]()


 - Versión de Salt instalada en los Minions:
    - salt '*' test.version
    - minionXXg:
    -  3000

![3.4.2]()
