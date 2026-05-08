# 🧠 SKILL: Gerenciamento de Contatos via Google Sheets

## 🎯 Objetivo

Permitir que o **JARVIS** identifique destinatários, recupere e-mails e valide informações de contato antes de realizar disparos via Gmail ou WhatsApp.

## 📊 Fonte de Dados (Database)

- **Nome do Arquivo:** `JARVIS_DATABASE_CONTACTS`
    
- **Página Principal:** `Contatos_Elite`
    
- **ID da Planilha:** `15vKu5Qb_T6tXMaC5x3ff0fKXGQHjEcqE-CiPQPy d5d8`
    

## 🛠️ Protocolo de Execução (Lookup)

1. **Gatilho:** Usuário solicita envio de mensagem/e-mail para um [Nome].
    
2. **Busca:** Consultar a coluna `B` (`NOME_COMPLETO`) buscando por correspondência exata ou parcial próxima.
    
3. **Extração:** Recuperar o valor da coluna `C` (`EMAIL_PRINCIPAL`).
    
4. **Fallback (Erro):** Se o nome não for encontrado, o Jarvis deve responder:
    
    > _"Senhor, não localizei o contato '[Nome]' na nossa base de dados. Gostaria de me ditar o e-mail para eu realizar o envio agora?"_
    

## 📜 Regras de Negócio (Business Rules)

- **Tom de Voz:** Sarcasmo fino, profissionalismo britânico (Estilo Jarvis/Iron Man).
    
- **Segurança:** Nunca enviar e-mails para endereços que não terminem em provedores válidos ou que pareçam suspeitos.
    
- **Privacidade:** Não ler em voz alta o e-mail completo se houver outras pessoas por perto (opcional conforme contexto).