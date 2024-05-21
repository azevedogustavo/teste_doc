# Fluxo Geral de funcionalidades Telessaude

```mermaid
  
  graph LR;
      Login([Login])

      Gerente[gerente] --> Login;
      %% linkStyle 0 stroke: blue; colorir a seta
      ps["Profssinal de saude"] --> Login;
      Admin[Administrador] --> Login;
      Login--> teleconsulta[Teleconsulta];
      Login--> cp[Cadastro de paciente];
      cp --> paciente[paciente];
      Login--> cps[Cadastro de profissionais de saúde];
      cps --> ps[Profissiona de saúde];
      Login--> cus[Cadastro de unidade de saúde];
      cus --> us[Unidade de saúde];
      Login--> Diagnostico[Telediagnóstico];
      teleconsulta ----> sc[/"Solicitar consulta"/];
      paciente -..-> sc;
      ps -..-> sc;
      especialidade[especialidade solicitada] --> sc;
      Diagnostico ----> telediagnostico[/"Registrar telediagnósico"/];

      paciente -..->telediagnostico;
      ps -..-> telediagnostico;

      telediagnostico --> laudo ;



```


```mermaid
  
  graph LR;

  Dependência[Atributo] -.-> |" \n dependência  "| saida[/"Método"/];



```

```mermaid
  
  graph LR;

  Dependência[informação] -.-> |" \n dependência  "| saida[/"Ação"/];



```

<br>
<br>

---

# Fluxo de consulta médica

```mermaid
  
  graph LR;

  Consulta[Teleconsulta] --> eventos["Eventos"];
  eventos --> visualizar[visualizar];
  visualizar --> entrar_na_sala[entrar na sala];



```


<br>
<br>

---

# Fluxo de Telediagnóstico

```mermaid
  
  graph LR;

  Consulta[Telediagnóstico] ---> Salvar[/"Salvar"/];
  Paciente -.-> Salvar;
  ProfissionalSolicitante[Profissional solicitante] -.-> Salvar;
  data[Data de realização do exame] -.-> Salvar;
  equipamento[Tipo do equipamento] -.-> Salvar;
  exame[Tipo do exame] -.-> Salvar;
  arquivo[Arquivo com o exame] -.-> Salvar;


```


<br>
<br>

---

# Fluxo de cadastro e unidades de saúde

```mermaid
  
  graph LR;

  UnidadesDeSaúde[Telediagnóstico] ---> CriarUnidadeSaude["Criar undiade de saúde"];
  CriarUnidadeSaude ---> |  Teleconsultoria,  Telediagnóstico, Tele-educação | Cadastrar[/"Cadastrar"/];
  NomeUnidadeSaude[Nome da unidade de saúde] -.-> Cadastrar;
  CNES -.-> Cadastrar;
```


<br>
<br>

---

# Fluxo de cadastro de profissionais de saúde

```mermaid
  
  graph LR;

  PofSaude[Profissionais de saúde] ---> Criarprofsaude["Criar Profissionais de saúde"] ---> Cadastrar[/"Cadastrar"/];
  NomeProfSaude[Nome do profssional de saúde] -.-> Cadastrar
  E-mailProfSaude[E-mail do prof. saúde] -.-> Cadastrar;
  UnidadeDeSaude[Unidade de Saúde] -.-> Cadastrar;
  CPF[CPF] -.-> Cadastrar;
  CRM[Registro do conselho de área profissional]-.-> Cadastrar;
  CNS[CNS] -.-> Cadastrar;
  CBO[Ocupação - Código CBO com 6 dígitos] -.-> Cadastrar;
  GrupoPermissão[Admin, Gerente, pediatra e Geriatra] -.-> Cadastrar;
  ProfSaudeTipo[Tipos de profssionas de saude] -.-> | profissional de saúde, PROVAB, Mais Médicos, Outros  |Cadastrar;
  Sexo[Sexo] -.-> |masculino, feminino, outros| Cadastrar;


```


<br>
<br>

---

# Fluxo de cadastro de paciente

```mermaid
  
  graph LR;

  Pacientes[Pacientes] ---> Criarprofsaude["Criar Pacientes"] ---> Cadastrar[/"Cadastrar paciente"/];

 Nome -.-> Cadastrar;
 E-mail -.-> Cadastrar;
 CPF -.-> Cadastrar;
 RG -.-> Cadastrar;
 Sexo -.-> Cadastrar;
 Telefone -.-> |whatsapp?| Cadastrar;

```
