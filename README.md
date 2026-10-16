# Meu Planner — PWA v1 (protótipo funcional)

## O que já está incluído
- Tela inicial em cartões com Tarefas, Hábitos, Metas, Financeiro, Listas e Diário/Calendário.
- Tarefas com data, horário opcional, categoria, prioridade Sim/Não, conclusão, edição e exclusão.
- Hábitos com frequência diária, dias da semana ou datas selecionadas; estado por data: Realizado, Não realizado, Ainda não registrado.
- Metas com prazo, situação e histórico automático de alterações de situação.
- Listas variadas com inclusão, conclusão e exclusão de itens.
- Financeiro com receitas, despesas, categoria, consulta mensal e totalização básica.
- Calendário mensal e consulta diária integrada, setas de navegação e indicador proporcional de hábitos realizados.
- PWA manifest e service worker básicos.

## Importante
Esta entrega é um protótipo inicial. Sem configurar o Supabase, a autenticação real e a sincronização online não ficam ativas. O modo local de demonstração usa o navegador deste dispositivo e não deve ser usado para dados pessoais ou financeiros reais.

## Teste local
Pode abrir `index.html` para uma inspeção visual, mas PWA/service worker exige servir por HTTPS ou localhost. Para testar rapidamente no computador, use um servidor local estático. O login de demonstração no modo sem Supabase é:
- E-mail: `demo@planner.local`
- Senha: `planner123`

Esse modo é apenas para demonstração; não representa uma conta real.

## Ativar Supabase
1. Crie um projeto em https://supabase.com/.
2. No SQL Editor, execute `supabase-schema.sql`.
3. Em Authentication, configure os métodos de e-mail e senha e o fluxo de recuperação de senha. Ajuste a URL de redirecionamento para o endereço publicado.
4. Copie a Project URL e a publishable/anon key do projeto.
5. Em `app.js`, preencha `SUPABASE_URL` e `SUPABASE_ANON_KEY`.
6. Não coloque service-role key ou qualquer segredo no frontend.
7. Teste com duas contas diferentes e confirme que cada conta só acessa os próprios dados.

## Publicar no GitHub Pages
1. Crie um repositório público no GitHub.
2. Envie os arquivos desta pasta para a raiz do repositório.
3. Em Settings → Pages, escolha a branch principal e a pasta raiz.
4. Configure as URLs permitidas no Supabase para o endereço do Pages.
5. Acesse por HTTPS, teste instalação, login, recuperação de senha e sincronização.

## Limitações conhecidas da v1
- O banco guarda o estado da aplicação como JSON por usuário para acelerar o protótipo; para crescer, convém normalizar tabelas e adicionar migrações.
- A sincronização salva o estado inteiro e é adequada apenas a uma primeira demonstração; conflitos entre vários dispositivos ainda precisam de uma estratégia mais robusta.
- O manifesto ainda não inclui ícones finais de instalação.
- Notificações push, lembretes, exportação/backup e sincronização offline robusta não estão implementados.
- A tela financeira calcula receitas e despesas do mês selecionado; o saldo anterior e o saldo acumulado ainda precisam ser especificados.
- Faça testes funcionais e de segurança antes de usar dados reais ou disponibilizar amplamente.
