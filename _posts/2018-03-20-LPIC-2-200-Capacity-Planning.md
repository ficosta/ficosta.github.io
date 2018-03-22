---
layout: post
title: LPIC 2 200 Capacity Planning
comments: true
---

Bora ae estudar um pouco de linux. Esse é o primeiro post de uma série que eu irei utilizar para estudar p/ minha prova LPI 201. Espero escrever sobre todos os tópicos.

## 200.1 Measure and Troubleshoot Resource Usage
#### Peso: 6

### Áreas de conhecimento:

* Medir uso da CPU
* Medir uso da memória
* Medir uso do disco I/O
* Medir uso da rede I/O
* Medir capacidade de transferencia do firewall e roteamento.
* Mapear o uso da rede.
* Combinar / correlacionar sintomas do sistema com prováveis problemas.
* Estimar o rendimento e identificar gargalos em um sistema, incluindo redes.

### Lista parcial dos arquivos, termos e utilitários usados:
* iostat
* iotop
* vmstat
* netstat
* ss
* iptraf
* pstree, ps
* w
* lsof
* top
* htop
* uptime
* sar
* swap
* processes blocked on I/O
* blocks in
* blocks out
* network
___
#### iostat

O comando [iostat](https://linux.die.net/man/1/iostat){:target="blank"} é utilizado para monitorar a carga de entrada/saída do sistema. Isso é feito observando o tempo que o dispositivo esta ativo em relação com a media da taxa de transferência.
Se nenhum parâmetro for utilizado é exibido as estatísticas desde o ultimo reboot. Os parâmetros mais comuns são [intervalo] [repetições].

``` bash
$ iostat [options] [interval [count] ]
```
