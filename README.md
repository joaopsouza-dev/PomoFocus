
# 🍅 PomoFocus

Aplicativo nativo para iOS voltado à produtividade e ao gerenciamento de tempo utilizando a técnica Pomodoro.

O PomoFocus tem como objetivo oferecer uma experiência simples e minimalista para organizar períodos de concentração, acompanhar sessões de estudo e visualizar métricas pessoais de produtividade.

O projeto está sendo desenvolvido em **Swift e SwiftUI**, com armazenamento local e sem necessidade de autenticação ou conexão com um backend.

## 🎯 Objetivo

Este projeto também tem um propósito educacional: explorar o desenvolvimento nativo para iOS, aprender os fundamentos de Swift e SwiftUI e construir uma aplicação funcional desde sua concepção até sua execução em um dispositivo físico.

## ✨ Funcionalidades

### Temporizador Pomodoro
- Contagem regressiva para períodos de foco.
- Iniciar, pausar e retomar sessões.
- Reiniciar ou finalizar o temporizador.
- Alternância entre períodos de foco e descanso.
- Indicador visual de progresso.

### Histórico de sessões
- Registro de sessões concluídas.
- Visualização de duração e horário.
- Armazenamento local dos registros.

### Estatísticas
- Tempo total de foco diário.
- Quantidade de sessões concluídas.
- Tempo acumulado de produtividade semanal.

### Configurações
- Personalização da duração dos períodos de foco.
- Configuração de descansos curtos e longos.
- Personalização da quantidade de sessões antes de um descanso longo.

> As funcionalidades serão implementadas gradualmente ao longo do desenvolvimento.

## 🛠️ Tecnologias

| Tecnologia | Utilização |
|---|---|
| Swift | Linguagem de programação |
| SwiftUI | Construção da interface |
| Foundation | Datas e funcionalidades fundamentais |
| Codable | Serialização e desserialização de dados |
| FileManager | Persistência local |
| XCTest | Testes automatizados |
| UserNotifications | Notificações locais |

## 🏗️ Arquitetura

O projeto utilizará uma arquitetura **MVVM (Model-View-ViewModel)** simplificada, buscando manter uma separação clara entre dados, interface e lógica de apresentação.

Estrutura planejada:

```text
PomoFocus/
├── App/
├── Models/
├── Views/
│   ├── Timer/
│   ├── History/
│   ├── Statistics/
│   └── Settings/
├── ViewModels/
├── Services/
└── Resources/
```

### Organização

- **Models:** estruturas que representam os dados da aplicação.
- **Views:** componentes e telas construídos com SwiftUI.
- **ViewModels:** gerenciamento de estados e lógica de apresentação.
- **Services:** operações de persistência e notificações.
- **App:** ponto de entrada da aplicação.

## 💾 Armazenamento

O PomoFocus não utilizará backend ou banco de dados remoto.

As informações serão armazenadas localmente no dispositivo, utilizando arquivos JSON e os recursos nativos de persistência do iOS.

## 📱 Plataforma

- Sistema operacional: iOS.
- Ambiente de desenvolvimento: Xcode.
- Interface: SwiftUI.

O aplicativo será inicialmente desenvolvido para uso pessoal, sem previsão de publicação na App Store.

## 🚀 Roadmap

O desenvolvimento será dividido nas seguintes etapas:

- [ ] Configuração inicial do projeto no Xcode.
- [ ] Estudo dos fundamentos de Swift.
- [ ] Construção da interface com SwiftUI.
- [ ] Implementação da arquitetura MVVM.
- [ ] Desenvolvimento do temporizador.
- [ ] Implementação da persistência local.
- [ ] Desenvolvimento do histórico de sessões.
- [ ] Implementação das estatísticas.
- [ ] Desenvolvimento das configurações.
- [ ] Implementação de notificações locais.
- [ ] Testes e ajustes.
- [ ] Instalação e validação em dispositivo físico.

## 📚 Objetivo de aprendizado

Ao longo do desenvolvimento, serão explorados conceitos como:

- Programação orientada a protocolos.
- Structs, classes e enums em Swift.
- Gerenciamento de estado com SwiftUI.
- Componentização de interfaces.
- Arquitetura MVVM.
- Manipulação de datas e temporizadores.
- Persistência de dados local.
- Ciclo de vida de aplicações iOS.
- Testes automatizados.

## 👨‍💻 Status

**Em desenvolvimento.**

Projeto pessoal e educacional, desenvolvido com o objetivo de aprender Swift e desenvolvimento nativo para iOS.
