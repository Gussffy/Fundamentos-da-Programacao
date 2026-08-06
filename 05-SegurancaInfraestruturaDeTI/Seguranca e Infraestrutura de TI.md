# Segurança de Infraestrutura de TI — Guia de Conteúdo

> Um resumo explicativo dos principais tópicos que serão estudados na disciplina, para te dar uma base antes das aulas começarem.

---

## 1. Do que trata a disciplina?

O objetivo central é estudar **estratégias de segurança** para proteger a infraestrutura de TI de uma organização contra ataques, danos e acessos não autorizados. Tudo gira em torno de garantir 4 pilares, conhecidos como **CIDA** (ou em inglês, *CIA + Authenticity*):

| Pilar | O que significa | Exemplo de ameaça |
|---|---|---|
| **Confidencialidade** | Só quem tem permissão acessa a informação | Vazamento de dados |
| **Integridade** | A informação não foi alterada indevidamente | Adulteração de dados em trânsito |
| **Disponibilidade** | O sistema está acessível quando necessário | Ataque de negação de serviço (DDoS) |
| **Autenticidade** | Garantir que quem acessa/envia é realmente quem diz ser | Falsificação de identidade (spoofing) |

Praticamente todo o conteúdo da disciplina (firewalls, IDS/IPS, políticas de acesso, normas ISO) existe para proteger esses quatro pilares.

---

## 2. Firewall e Arquitetura Segura de Rede

### 2.1 O que é um Firewall
Um firewall é um dispositivo (físico ou software) que **filtra o tráfego de rede**, permitindo ou bloqueando pacotes de dados com base em regras pré-definidas. É a primeira linha de defesa entre uma rede interna (confiável) e uma rede externa (não confiável, como a internet).

**Tipos principais que você provavelmente vai estudar:**
- **Filtro de pacotes (packet filtering)** — analisa apenas cabeçalhos (IP, porta) sem entender o contexto da conexão.
- **Firewall de estado (stateful)** — acompanha o estado da conexão inteira (mais inteligente e seguro que o filtro simples).
- **Firewall de aplicação / proxy** — analisa o conteúdo no nível da aplicação (ex: HTTP), permitindo regras mais refinadas.
- **Next-Generation Firewall (NGFW)** — combina filtragem tradicional com IPS, inspeção profunda de pacotes (DPI) e reconhecimento de aplicações.

### 2.2 Arquitetura Segura de Rede
Não basta ter um firewall — a forma como a rede é **desenhada** também é uma camada de proteção. Conceitos importantes:
- **DMZ (Zona Desmilitarizada)** — uma sub-rede isolada onde ficam servidores expostos à internet (ex: servidor web), separando-os da rede interna sensível.
- **Segmentação de rede** — dividir a rede em partes menores (VLANs, sub-redes) para limitar o alcance de um invasor caso ele comprometa um ponto.
- **Defesa em profundidade (defense in depth)** — usar várias camadas de proteção, para que a falha de uma não comprometa tudo.

---

## 3. Elementos de Rede (Switches, Roteadores, etc.)

Antes de proteger a rede, é preciso entender seus componentes básicos:
- **Roteador** — encaminha pacotes entre redes diferentes (ex: rede interna ↔ internet). Ponto crítico de segurança, pois é a "porta de entrada".
- **Switch** — conecta dispositivos dentro da mesma rede local, encaminhando tráfego com base no endereço MAC.
- **VLAN (Virtual LAN)** — segmentação lógica da rede feita no switch, permitindo isolar tráfego mesmo em uma mesma infraestrutura física.

Entender como esses equipamentos funcionam é pré-requisito para entender onde e como aplicar firewalls, IDS/IPS e políticas de acesso.

---

## 4. Patches de Segurança e Baseline

### 4.1 Patches de Segurança
Correções lançadas por fabricantes de software/sistemas para corrigir **vulnerabilidades conhecidas**. Manter um sistema sem patches é uma das causas mais comuns de invasões — muitos ataques exploram falhas que já têm correção disponível, mas que não foi aplicada.
- **Gestão de patches (patch management)** — processo estruturado de identificar, testar e aplicar atualizações de segurança de forma controlada, sem quebrar sistemas em produção.

### 4.2 Baseline (linha de base)
Uma configuração de referência considerada seguraque serve de **padrão mínimo** para todos os sistemas de uma organização (ex: configurações de firewall, senhas, serviços desnecessários desativados). Serve para:
- Garantir consistência entre servidores/estações.
- Facilitar a detecção de desvios (algo fora do baseline pode indicar comprometimento).

---

## 5. IPS, IDS, Antivírus, Antispam e Proxy

### 5.1 IDS vs. IPS
Dois conceitos que costumam confundir no começo:
- **IDS (Intrusion Detection System)** — **detecta** e alerta sobre atividades suspeitas, mas não bloqueia sozinho. É passivo — funciona como um "alarme".
- **IPS (Intrusion Prevention System)** — além de detectar, **bloqueia ativamente** o tráfego malicioso em tempo real. É o "alarme + porta trancando sozinha".

Ambos analisam tráfego em busca de assinaturas de ataques conhecidos ou comportamentos anômalos.

### 5.2 Antivírus
Software que detecta, bloqueia e remove **malware** (vírus, trojans, ransomware, etc.), geralmente por meio de:
- **Assinaturas** — comparação com um banco de malwares conhecidos.
- **Heurística/comportamento** — detecção de comportamento suspeito, mesmo sem assinatura conhecida (importante contra ameaças novas, "zero-day").

### 5.3 Antispam
Filtra e-mails indesejados/maliciosos (spam, phishing), reduzindo um dos vetores de ataque mais comuns: o **phishing**, onde o invasor tenta enganar o usuário para roubar credenciais ou instalar malware.

### 5.4 Proxy
Um servidor intermediário entre o usuário e a internet. Dois tipos importantes:
- **Proxy direto (forward proxy)** — intermedia requisições saindo da rede interna para a internet (ex: controle de acesso a sites, cache).
- **Proxy reverso (reverse proxy)** — intermedia requisições vindas de fora em direção a servidores internos, escondendo a infraestrutura real e podendo distribuir carga (load balancing).

---

## 6. Políticas de Segurança e Controle de Acesso

### 6.1 Políticas de Segurança
Documentos formais que definem **regras, responsabilidades e procedimentos** de segurança da informação dentro de uma organização — desde uso aceitável de recursos até resposta a incidentes. É a base "de papel" que orienta todas as medidas técnicas.

### 6.2 Controle de Acesso
Mecanismos que garantem que **só pessoas autorizadas acessem determinados recursos**. Modelos clássicos que costumam aparecer:
- **DAC (Discretionary Access Control)** — o dono do recurso decide quem acessa.
- **MAC (Mandatory Access Control)** — controle centralizado por políticas fixas (comum em ambientes militares/governamentais).
- **RBAC (Role-Based Access Control)** — acesso baseado no **papel/função** do usuário na organização (o mais usado no mercado corporativo).

Princípios importantes ligados a isso:
- **Princípio do menor privilégio** — cada usuário/sistema deve ter só o acesso mínimo necessário para sua função.
- **Autenticação multifator (MFA)** — combinar múltiplos fatores (senha + token/biometria) para reduzir risco de acesso indevido.

---

## 7. Normas da Família ISO/IEC 27001 e ISO/IEC 27002

Duas normas centrais em Segurança da Informação, frequentemente cobradas em provas e usadas no mercado:

- **ISO/IEC 27001** — define os **requisitos** para implementar um **SGSI (Sistema de Gestão de Segurança da Informação)**. É a norma **certificável** — uma empresa pode obter certificação ISO 27001.
- **ISO/IEC 27002** — é um **código de boas práticas**, com um catálogo de controles de segurança (ex: controles de acesso, criptografia, segurança física) que apoiam a implementação da 27001. Não é certificável por si só — é um guia complementar.

**Analogia simples:** a 27001 diz "você precisa ter um sistema de gestão de segurança e ele precisa atender esses requisitos"; a 27002 diz "aqui está um catálogo de boas práticas que você pode usar para atender esses requisitos".

---

## 8. Requisitos de Qualidade, Riscos Associados e Medidas Defensivas

Esse bloco trata da lógica de **gestão de risco**, que é o raciocínio por trás de toda decisão em segurança da informação:

```
Risco = Probabilidade (ameaça explorando uma vulnerabilidade) × Impacto
```

Conceitos-chave:
- **Ameaça** — algo que pode causar dano (ex: um invasor, um vírus, uma falha de energia).
- **Vulnerabilidade** — uma fraqueza que pode ser explorada (ex: sistema desatualizado, senha fraca).
- **Risco** — a combinação entre ameaça + vulnerabilidade, ponderada pelo impacto potencial.
- **Medidas defensivas (controles)** — ações para reduzir o risco, que podem ser:
    - **Preventivas** — evitam que o incidente aconteça (ex: firewall, patch).
    - **Detectivas** — identificam quando algo já está acontecendo (ex: IDS).
    - **Corretivas/reativas** — atuam depois do incidente para reduzir o dano (ex: plano de contingência, backup).

Esse raciocínio de risco é essencial também para o objetivo de aprendizagem de **elaborar plano de contingência** — ou seja, ter um plano definido de resposta caso algo dê errado (física ou logicamente), incluindo backup, redundância e recuperação de desastres (disaster recovery).

---

## 9. Resumo Visual

| Camada de defesa | Ferramentas/Conceitos |
|---|---|
| Perímetro de rede | Firewall, DMZ, Proxy |
| Detecção/Prevenção | IDS, IPS, Antivírus, Antispam |
| Controle de pessoas | Políticas de segurança, Controle de Acesso (DAC/MAC/RBAC), MFA |
| Manutenção contínua | Patches de segurança, Baseline |
| Governança | ISO/IEC 27001 (requisitos) e ISO/IEC 27002 (boas práticas) |
| Gestão de risco | Identificação de ameaças/vulnerabilidades, medidas defensivas, plano de contingência |

---

## 10. Glossário Rápido

- **Malware** — termo genérico para software malicioso (vírus, worm, trojan, ransomware, spyware).
- **Phishing** — tentativa de engano (geralmente por e-mail) para roubar credenciais ou instalar malware.
- **Zero-day** — vulnerabilidade recém-descoberta, ainda sem correção disponível.
- **DDoS** — ataque de negação de serviço distribuído, que sobrecarrega um sistema para tirá-lo do ar.
- **SGSI** — Sistema de Gestão de Segurança da Informação (o que a ISO 27001 exige que seja implementado).
- **Disaster Recovery (DR)** — conjunto de processos para restaurar sistemas após um desastre.
- **Hardening** — processo de reduzir a superfície de ataque de um sistema (desativar serviços desnecessários, aplicar configurações seguras).

---

## 11. Dicas para começar bem o semestre

- **Revise fundamentos de redes** (modelo OSI/TCP-IP, portas, protocolos como TCP/UDP, HTTP/HTTPS, DNS) — é praticamente impossível entender firewall, IDS/IPS e proxy sem essa base.
- **Familiarize-se com o vocabulário de segurança em inglês** — grande parte da documentação técnica, CVEs (vulnerabilidades catalogadas) e material de referência está em inglês.
- **Dê uma olhada geral na ISO/IEC 27001 e 27002** antes das aulas sobre o tema — mesmo um resumo rápido ajuda muito a acompanhar, já que são normas extensas.
- **Pratique em ambiente controlado**: ferramentas como **pfSense** (firewall open-source), **Wireshark** (análise de tráfego) e VMs isoladas (VirtualBox/VMware) são ótimas para experimentar os conceitos na prática sem risco.
- **Pense sempre em "camadas"**: segurança de infraestrutura raramente depende de uma única ferramenta — o raciocínio de **defesa em profundidade** (várias camadas se complementando) é o fio condutor de quase todo o conteúdo.