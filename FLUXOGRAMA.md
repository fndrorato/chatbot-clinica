# 🗺️ Fluxograma - Chatbot Odontológico

## Visualização do Fluxo Completo de Conversação

```mermaid
flowchart TD
    Start([👋 Início - Saudação]) --> CheckPatient{Já é paciente?}
    
    CheckPatient -->|✅ Sim| ValidateCPF[📝 Validar CPF/Tel]
    CheckPatient -->|🆕 Não| NewPatient[📋 Cadastro Novo Paciente]
    
    NewPatient --> CollectName[Nome Completo]
    CollectName --> CollectCPF[CPF]
    CollectCPF --> CollectPhone[Telefone]
    CollectPhone --> CollectBirth[Data Nascimento]
    CollectBirth --> ConsultType
    
    ValidateCPF --> ConsultType{Tipo de Consulta?}
    
    ConsultType -->|1️⃣ Primeira vez| ChooseDentist
    ConsultType -->|2️⃣ Retorno| ChooseDentist
    ConsultType -->|3️⃣ Emergência| Emergency[🚨 Fluxo Emergência]
    ConsultType -->|4️⃣ Limpeza| ChooseDentist
    ConsultType -->|5️⃣ Outro| ChooseDentist
    
    Emergency --> EmergencyContact[📞 Contato Urgência<br/>+ Endereço]
    EmergencyContact --> End
    
    ChooseDentist[👨‍⚕️ Escolha Dentista]
    ChooseDentist --> DentistOptions{Qual dentista?}
    
    DentistOptions -->|Dra. Maria - Ortod.| CheckInsurance
    DentistOptions -->|Dr. João - Geral| CheckInsurance
    DentistOptions -->|Dr. Pedro - Impl.| CheckInsurance
    DentistOptions -->|Dra. Ana - Endo.| CheckInsurance
    DentistOptions -->|Qualquer um| CheckInsurance
    
    CheckInsurance{Tem convênio?}
    
    CheckInsurance -->|✅ Sim| InsuranceType[Qual convênio?]
    CheckInsurance -->|❌ Não| TimePref
    
    InsuranceType --> InsuranceList{Escolher}
    InsuranceList -->|Unimed| InsuranceCard
    InsuranceList -->|Bradesco| InsuranceCard
    InsuranceList -->|SulAmérica| InsuranceCard
    InsuranceList -->|Amil| InsuranceCard
    InsuranceList -->|Outro| InsuranceCard
    
    InsuranceCard[📄 Nº Carteirinha] --> TimePref
    
    TimePref[🕐 Preferência Horário]
    TimePref --> TimeOptions{Período?}
    
    TimeOptions -->|☀️ Manhã| DayPref
    TimeOptions -->|🌤️ Tarde| DayPref
    TimeOptions -->|🌙 Noite| DayPref
    TimeOptions -->|🤷 Tanto faz| DayPref
    
    DayPref[📅 Preferência Dia]
    DayPref --> DayOptions{Dia semana?}
    
    DayOptions -->|Segunda| ShowSlots
    DayOptions -->|Terça| ShowSlots
    DayOptions -->|Quarta| ShowSlots
    DayOptions -->|Quinta| ShowSlots
    DayOptions -->|Sexta| ShowSlots
    DayOptions -->|Sábado| ShowSlots
    DayOptions -->|Qualquer dia| ShowSlots
    
    ShowSlots[📋 Mostrar Horários<br/>Disponíveis]
    ShowSlots --> ChooseSlot{Escolher Horário}
    
    ChooseSlot -->|Slot 1| ConfirmBooking
    ChooseSlot -->|Slot 2| ConfirmBooking
    ChooseSlot -->|Slot 3| ConfirmBooking
    ChooseSlot -->|Ver mais| ShowSlots
    
    ConfirmBooking[✅ Resumo Agendamento]
    ConfirmBooking --> FinalConfirm{Confirmar?}
    
    FinalConfirm -->|✅ Confirmar| BookingSuccess
    FinalConfirm -->|🔄 Alterar| ShowSlots
    FinalConfirm -->|❌ Cancelar| CancelFlow
    
    BookingSuccess[🎉 Agendamento OK!]
    BookingSuccess --> SendConfirm[📲 Enviar:<br/>✅ SMS<br/>✅ Email<br/>✅ Calendar]
    SendConfirm --> PostBooking{O que fazer?}
    
    PostBooking -->|📍 Ver local| MapLink[🗺️ Google Maps]
    PostBooking -->|📅 Add calendário| CalendarLink[📅 Google Calendar]
    PostBooking -->|💬 Menu| Start
    PostBooking -->|❌ Sair| End
    
    CancelFlow[❌ Cancelado] --> End
    
    MapLink --> End
    CalendarLink --> End
    
    End([👋 Fim])
    
    style Start fill:#667eea,color:#fff
    style End fill:#667eea,color:#fff
    style BookingSuccess fill:#10b981,color:#fff
    style Emergency fill:#ef4444,color:#fff
    style CheckPatient fill:#f59e0b,color:#000
    style ConsultType fill:#f59e0b,color:#000
    style CheckInsurance fill:#f59e0b,color:#000
    style FinalConfirm fill:#f59e0b,color:#000
```

---

## 📝 Legenda

| Cor | Significado |
|-----|-------------|
| 🟣 Roxo | Início/Fim do fluxo |
| 🟢 Verde | Sucesso (Agendamento confirmado) |
| 🔴 Vermelho | Emergência |
| 🟠 Laranja | Pontos de decisão importantes |
| ⬜ Branco | Ações e processos normais |

---

## 🔄 Fluxos Principais

### 1️⃣ Paciente Existente
```
Início → Validar CPF → Tipo Consulta → Escolher Dentista → ... → Agendamento
```

### 2️⃣ Paciente Novo
```
Início → Cadastro (4 etapas) → Tipo Consulta → Escolher Dentista → ... → Agendamento
```

### 3️⃣ Emergência
```
Início → Tipo Consulta → EMERGÊNCIA → Contato Urgente → Fim
```

---

## 📊 Estatísticas do Fluxo

- **Total de etapas:** ~15 passos
- **Tempo estimado:** 2-3 minutos
- **Pontos de decisão:** 8
- **Saídas alternativas:** 3 (Emergência, Cancelamento, Ver mapa)
- **Taxa de conclusão esperada:** 70-80%

---

## 🛠️ Como Editar

### Online (sem instalar nada):
1. Acesse [Mermaid Live Editor](https://mermaid.live)
2. Cole o código acima
3. Edite visualmente
4. Exporte como PNG/SVG/PDF

### Localmente:
1. Instale extensão Mermaid no VS Code
2. Edite este arquivo `.md`
3. Visualize em tempo real

### GitHub:
- GitHub renderiza Mermaid automaticamente
- Basta fazer commit deste arquivo
- Visualize direto no repositório

---

## 💡 Dicas de Personalização

### Adicionar novo passo:
```mermaid
NovoPasso[📝 Descrição] --> ProximoPasso
```

### Mudar cores:
```mermaid
style NovoPasso fill:#cor,color:#texto
```

### Cores disponíveis:
- `#667eea` - Roxo (Início/Fim)
- `#10b981` - Verde (Sucesso)
- `#ef4444` - Vermelho (Erro/Emergência)
- `#f59e0b` - Laranja (Decisões)
- `#3b82f6` - Azul (Informação)

---

⭐ **Dica:** Este fluxograma é 100% editável! Adapte para sua clínica.
