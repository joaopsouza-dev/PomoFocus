
# PomoFocus — Roadmap de Desenvolvimento

Aplicativo nativo de produtividade para iOS, desenvolvido em Swift e SwiftUI.

## 1. Visão geral

O FocusTime será um aplicativo pessoal de gerenciamento de tempo baseado na técnica Pomodoro.

O objetivo é desenvolver uma aplicação nativa para iPhone, sem autenticação, backend ou dependências externas.

### Objetivos técnicos

- Aprender Swift e SwiftUI.
- Familiarizar-se com o Xcode.
- Construir interfaces nativas para iOS.
- Trabalhar com estados e eventos.
- Implementar lógica de temporização.
- Persistir informações localmente.
- Organizar o código com separação de responsabilidades.
- Executar o aplicativo em um iPhone físico.

## 2. Stack tecnológica

| Tecnologia | Utilização |
|---|---|
| Swift | Linguagem principal |
| SwiftUI | Interface gráfica |
| Foundation | Datas, tempo e estruturas fundamentais |
| Codable | Serialização dos dados |
| FileManager | Armazenamento local |
| XCTest | Testes automatizados |
| UserNotifications | Notificações locais, em etapa posterior |

Não utilizaremos backend, APIs externas, autenticação ou banco de dados remoto.

## 3. Funcionalidades previstas

### 3.1 Timer

- Contagem regressiva.
- Iniciar temporizador.
- Pausar temporizador.
- Retomar temporizador.
- Reiniciar temporizador.
- Finalizar sessão antecipadamente.
- Indicador visual de progresso.
- Alternância entre foco e descanso.

### 3.2 Histórico

- Registrar sessões concluídas.
- Exibir data e horário.
- Exibir duração de cada sessão.
- Consultar sessões anteriores.

### 3.3 Estatísticas

- Tempo total de foco no dia.
- Quantidade de sessões concluídas.
- Tempo total de foco na semana.
- Histórico de produtividade.

### 3.4 Configurações

- Personalizar duração do foco.
- Personalizar descanso curto.
- Personalizar descanso longo.
- Configurar quantidade de sessões antes do descanso longo.

## 4. Arquitetura e organização

Utilizaremos uma arquitetura MVVM simplificada.

A intenção não é reproduzir toda a estrutura de um backend Spring Boot, mas separar interface, estado, dados e operações.

### Estrutura de diretórios

```text
FocusTime/
│
├── App/
│   └── FocusTimeApp.swift
│
├── Models/
│   ├── FocusSession.swift
│   └── TimerConfiguration.swift
│
├── Views/
│   ├── Timer/
│   │   └── TimerView.swift
│   │
│   ├── History/
│   │   └── HistoryView.swift
│   │
│   ├── Statistics/
│   │   └── StatisticsView.swift
│   │
│   └── Settings/
│       └── SettingsView.swift
│
├── ViewModels/
│   └── TimerViewModel.swift
│
├── Services/
│   ├── SessionStorage.swift
│   └── NotificationService.swift
│
└── Resources/
```

### Responsabilidades

**Models**

Representam as estruturas de dados utilizadas pelo aplicativo.

**Views**

Responsáveis pela apresentação visual e interação com o usuário.

**ViewModels**

Controlam estados, eventos e regras de apresentação das telas.

**Services**

Responsáveis por operações específicas, como persistência e notificações.

**App**

Ponto de entrada da aplicação.

## 5. Modelagem inicial

### FocusSession

Representa uma sessão de foco concluída.

Propriedades previstas:

- id: UUID
- duration: Int
- completedAt: Date

Exemplo conceitual:

```swift
struct FocusSession: Identifiable, Codable {
    var id: UUID
    var duration: Int
    var completedAt: Date
}
```

### TimerConfiguration

Representa as preferências do temporizador.

Propriedades previstas:

- focusDuration: Int
- shortBreakDuration: Int
- longBreakDuration: Int
- sessionsBeforeLongBreak: Int

## 6. Persistência local

Inicialmente utilizaremos armazenamento local com arquivos JSON.

O `Codable` permitirá converter nossos modelos para JSON, enquanto o `FileManager` permitirá salvar e recuperar os arquivos.

O armazenamento ficará dentro do diretório Application Support do aplicativo.

Essa abordagem é simples, não exige banco de dados e permite trabalhar com uma estrutura organizada.

O UserDefaults poderá ser utilizado para preferências simples, caso seja conveniente.

Não utilizaremos SwiftData ou Core Data nesta primeira versão.

---

# 7. Roadmap de implementação

## FASE 01 — Configuração do ambiente

### Objetivo

Criar o projeto e entender o funcionamento básico do Xcode.

### Atividades

- [ ] Criar um projeto iOS no Xcode.
- [ ] Selecionar Swift como linguagem.
- [ ] Selecionar SwiftUI como interface.
- [ ] Configurar o nome FocusTime.
- [ ] Definir identificador do aplicativo.
- [ ] Conhecer a estrutura inicial do projeto.
- [ ] Executar o aplicativo no simulador.
- [ ] Conhecer o funcionamento do Preview do SwiftUI.

### Critério de conclusão

Aplicativo inicial executando corretamente no simulador.

## FASE 02 — Fundamentos de Swift

### Objetivo

Aprender os conceitos necessários para desenvolver o aplicativo.

### Conteúdos

- [ ] Variáveis e constantes.
- [ ] Tipos de dados.
- [ ] Optionals.
- [ ] Condicionais.
- [ ] Estruturas de repetição.
- [ ] Funções.
- [ ] Structs e Classes.
- [ ] Enums.
- [ ] Protocols.
- [ ] Extensions.
- [ ] Closures.
- [ ] Arrays e Dictionaries.
- [ ] Tratamento de erros.
- [ ] Codable.

### Critério de conclusão

Conseguir criar estruturas de dados, funções e operações básicas em Swift sem depender constantemente de exemplos.

## FASE 03 — Primeira interface com SwiftUI

### Objetivo

Construir a primeira versão visual do aplicativo.

### Conteúdos

- [ ] Text.
- [ ] Button.
- [ ] VStack.
- [ ] HStack.
- [ ] ZStack.
- [ ] Spacer.
- [ ] Padding.
- [ ] Background.
- [ ] ForegroundStyle.
- [ ] Shapes.
- [ ] Modifiers.
- [ ] @State.
- [ ] Componentização de Views.

### Implementação

Criar a tela principal contendo:

- Nome do aplicativo.
- Temporizador circular.
- Tempo restante.
- Botão iniciar.
- Botão pausar.
- Botão reiniciar.

### Critério de conclusão

Interface funcional e visualmente organizada, mesmo que o temporizador ainda não tenha sua lógica definitiva.

## FASE 04 — Arquitetura MVVM

### Objetivo

Separar a interface da lógica de funcionamento.

### Atividades

- [ ] Criar diretórios Models, Views, ViewModels e Services.
- [ ] Criar FocusSession.
- [ ] Criar TimerConfiguration.
- [ ] Criar TimerViewModel.
- [ ] Entender Observable e @State.
- [ ] Conectar a View ao ViewModel.
- [ ] Centralizar os estados do temporizador.

### Critério de conclusão

A View não deve concentrar toda a lógica do temporizador.

## FASE 05 — Implementação do temporizador

### Objetivo

Construir a funcionalidade principal do FocusTime.

### Atividades

- [ ] Implementar contagem regressiva.
- [ ] Implementar iniciar.
- [ ] Implementar pausar.
- [ ] Implementar retomar.
- [ ] Implementar reiniciar.
- [ ] Implementar finalização automática.
- [ ] Implementar progresso visual.
- [ ] Implementar alternância entre foco e descanso.

### Consideração técnica importante

O temporizador não deverá depender exclusivamente de um contador que diminui a cada segundo.

Utilizaremos uma data de término (`Date`) como referência.

O tempo restante será calculado pela diferença entre a data atual e a data de término.

Isso evita inconsistências quando o aplicativo é suspenso, minimizado ou volta a ser aberto.

### Critério de conclusão

Temporizador funcionando corretamente durante a execução, pausa, retomada e retorno ao aplicativo.

## FASE 06 — Persistência de dados

### Objetivo

Salvar informações localmente.

### Atividades

- [ ] Criar SessionStorage.
- [ ] Implementar serialização JSON.
- [ ] Implementar gravação de sessões.
- [ ] Implementar recuperação de sessões.
- [ ] Implementar exclusão de registros, se necessário.
- [ ] Persistir configurações.
- [ ] Testar fechamento e reabertura do aplicativo.

### Critério de conclusão

As sessões concluídas e configurações devem continuar disponíveis após fechar e abrir o aplicativo.

## FASE 07 — Histórico de sessões

### Objetivo

Permitir consultar os períodos de foco anteriores.

### Atividades

- [ ] Criar HistoryView.
- [ ] Exibir lista de sessões.
- [ ] Exibir duração.
- [ ] Exibir data e horário.
- [ ] Organizar registros por data.
- [ ] Tratar histórico vazio.

### Critério de conclusão

Usuário consegue visualizar todas as sessões concluídas e armazenadas.

## FASE 08 — Estatísticas

### Objetivo

Apresentar informações sobre produtividade.

### Atividades

- [ ] Criar StatisticsView.
- [ ] Calcular tempo focado no dia.
- [ ] Calcular quantidade de sessões.
- [ ] Calcular tempo focado na semana.
- [ ] Organizar os dados por período.
- [ ] Criar componentes visuais para apresentar os resultados.

### Critério de conclusão

Estatísticas calculadas a partir dos registros persistidos, sem armazenar informações redundantes.

## FASE 09 — Configurações

### Objetivo

Permitir personalização do Pomodoro.

### Atividades

- [ ] Criar SettingsView.
- [ ] Configurar duração do foco.
- [ ] Configurar descanso curto.
- [ ] Configurar descanso longo.
- [ ] Configurar quantidade de sessões.
- [ ] Salvar preferências.
- [ ] Aplicar configurações ao temporizador.

### Critério de conclusão

Alterações nas configurações devem permanecer salvas e ser utilizadas nas próximas sessões.

## FASE 10 — Ciclo de vida e notificações

### Objetivo

Melhorar o funcionamento do aplicativo fora da tela principal.

### Atividades

- [ ] Validar comportamento ao bloquear o iPhone.
- [ ] Validar comportamento ao minimizar o aplicativo.
- [ ] Recuperar corretamente o tempo restante.
- [ ] Implementar notificações locais.
- [ ] Solicitar permissão de notificações.
- [ ] Notificar conclusão de sessões.

### Critério de conclusão

O usuário deve conseguir iniciar uma sessão, sair do aplicativo e receber uma notificação quando o tempo terminar, respeitando as limitações do iOS.

## FASE 11 — Testes e qualidade

### Objetivo

Garantir o funcionamento das principais funcionalidades.

### Atividades

- [ ] Testar iniciar e pausar.
- [ ] Testar retomada.
- [ ] Testar finalização.
- [ ] Testar persistência.
- [ ] Testar recuperação dos dados.
- [ ] Testar cálculos estatísticos.
- [ ] Testar configurações.
- [ ] Criar testes unitários para regras importantes.

### Critério de conclusão

Principais funcionalidades funcionando sem erros conhecidos.

## FASE 12 — Acabamento e instalação

### Objetivo

Finalizar a primeira versão utilizável.

### Atividades

- [ ] Definir identidade visual.
- [ ] Criar ícone do aplicativo.
- [ ] Ajustar tipografia.
- [ ] Melhorar animações.
- [ ] Revisar espaçamentos.
- [ ] Testar em diferentes tamanhos de tela.
- [ ] Instalar no iPhone físico.
- [ ] Validar funcionamento fora do simulador.

### Critério de conclusão

FocusTime funcionando como aplicativo nativo no iPhone.

---

# 8. Escopo fora da primeira versão

Para evitar complexidade desnecessária, não implementaremos inicialmente:

- Cadastro e autenticação.
- Backend.
- Banco de dados remoto.
- Sincronização entre dispositivos.
- Integração com redes sociais.
- Compartilhamento de produtividade.
- Inteligência artificial.
- Widgets.
- Apple Watch.
- Publicação na App Store.

Essas funcionalidades poderão ser consideradas em versões futuras.

# 9. Ordem de desenvolvimento

A ordem de implementação será:

1. Configuração do Xcode.
2. Fundamentos de Swift.
3. Interface inicial.
4. Modelagem de dados.
5. Arquitetura MVVM.
6. Lógica do temporizador.
7. Persistência local.
8. Histórico.
9. Estatísticas.
10. Configurações.
11. Ciclo de vida e notificações.
12. Testes.
13. Acabamento.
14. Instalação no iPhone.

# 10. Metodologia de desenvolvimento

O projeto será desenvolvido incrementalmente.

Para cada etapa:

1. Entender o problema.
2. Identificar os conceitos necessários.
3. Planejar a implementação.
4. Implementar uma funcionalidade por vez.
5. Executar no Xcode.
6. Testar o comportamento.
7. Revisar o código.
8. Avançar para a próxima etapa.

Não avançaremos automaticamente apenas porque o código compila. Cada funcionalidade deverá ser compreendida e validada.

## 11. Resultado esperado

Ao finalizar o projeto, teremos um aplicativo nativo para iOS com:

- Temporizador Pomodoro funcional.
- Controle de foco e descanso.
- Histórico persistente.
- Estatísticas de produtividade.
- Configurações personalizáveis.
- Armazenamento local.
- Interface construída com SwiftUI.
- Código organizado e testável.

**Objetivo principal:** concluir um primeiro projeto nativo em Swift, adquirindo fundamentos suficientes para desenvolver aplicações iOS mais completas no futuro.
