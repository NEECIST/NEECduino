# Como programar os componentes?
O NEECduino usa um *PIC18F14K50* e um *ATMega328*. Ambos precisam de ser programados para o seu correto funcionamento.

## Como programar o PIC?
**NOTA:** Todos os passos devem ser feitos na primeira vez, após isso basta repetir o passo 5.
### 1. Confirmar a instalação do pk2cmd
Num terminal, confirma se está instalado, executando:
`pk2cmd`
Se aparecer uma mensagem semelhante a: `bash: /usr/local/bin/pk2cmd: No such file or directory` deves proceder à instalação do mesmo, executando o script `install.sh`, que se encontra na diretoria `pk2cmd`. Se aparecer um menu de ajuda, o programa está instado.

### 2. Verificar ligação do PicKit ao PC
Num terminal, na diretoria `pk2cmd` (muito importante estar nesta diretoria), executa o script `check.sh`.
Deve aparecer um output semelhante ao seguinte (as versões poderão variar):
```
Checking PicKit2 connection...

Executable Version:    1.21.00
Device File Version:   1.62.14
OS Firmware Version:   2.32.00


Operation Succeeded
```
Possíveis erros:

- Se aparecer a mensagem `PK2DeviceFile.dat device file not found.` verifica se o ficheiro `PK2DeviceFile.dat` está presente na diretoria atual.
- Se aparecer a mensagem `OS Firmware Version:   PICkit 2 not found` verifica se o PicKit está ligado ao computador e tem o LED Power acesso a verde.

### 3. Ligar o Pic ao PicKit
Realizar as ligações conforme indicado na tabela abaixo. Vê as imagens para saber a numeração dos pins.
Programador | Chip
-------|-------
1 (VPP) | 4 (VPP)
2 (VDD) | 1 (VDD)
3 (VSS) | 20 (VSS)
4 (PGD) | 19 (PGD)
5 (PGC) | 18 (PGC)

### 4. Assegurar a correta ligação entre o Pic e o PicKit/PC
Executa o script `detect.sh` e deverás receber a seguinte mensagem: `Auto-Detect: Found part PIC18F14K50.` Se não receberes uma informação igual, verifica se o Pic está bem ligado e a versão do Pic é a correta.

### 5. Programa o Pic com o código necessário para o NEECduino
Executa o script `program.sh`. Se receberes o output `Program Succeeded.` o Pic foi programado. De vez em quando (para alguns Pic) testa se o mesmo ficou bem programado, utilizando um NEECduino e tentando fazer upload de código para o mesmo. Se tal funcionar, o Pic está programado.

### Extra: Apagar a memória do Pic
Executa o script `erase.sh` e deverá dar a mensagem de `Operation Succeeded`


## Como programar o ATMega?
Fonte: [arduino.cc](https://www.arduino.cc/en/Tutorial/ArduinoISP)

### 1. Configurar programador

- Em Tools > Board e Serial Port, selecionar a placa que será usada como programador (Arduino UNO).
- Carregar o exemplo ArduinoISP para a placa de programador

### 3. Montagem
Efetuar a montagem entre arduinos:

<img src="https://www.arduino.cc/en/uploads/Tutorial/ArduinoUNOtoUNO_ISP2.jpg" data-canonical-src="https://www.arduino.cc/en/uploads/Tutorial/ArduinoUNOtoUNO_ISP2.jpg" width="400" />


### 2. Gravar Bootloader

- Em Tools > Board , selecionar a placa que será usada onde se encontra o ATMEGA (Arduino UNO) por programar
- Selecionar Arduino as ISP em Tools > Programmer.
- Usar o comando Burn Bootloader.

