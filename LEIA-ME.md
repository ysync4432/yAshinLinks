# Luxury’ Events · Firebase + Netlify

Arquivos (todos na raiz, sem pastas):

- `index.html` · site público
- `admin.html` · painel (fica em `seusite.netlify.app/admin`)
- `firebase-config.js` · dados do seu projeto Firebase
- `firestore.rules` · regras do banco (você cola no console do Firebase, não sobe na Netlify)

## 1. Firebase (console.firebase.google.com)

1. **Criar projeto** (pode desligar o Google Analytics).
2. **Build → Firestore Database → Criar banco de dados** → modo produção.
3. **Build → Authentication → Começar → E-mail/senha → Ativar.**
4. Na aba **Usuários → Adicionar usuário**: em e-mail digite `SEUUSUARIO@painel.local` (troque SEUUSUARIO pelo nome que quiser, sem espaços) e uma senha forte (mínimo 6 caracteres). Copie o **UID do usuário**.
5. **Firestore → Regras**: cole o conteúdo de `firestore.rules`, troque `COLE_SEU_UID` pelo UID copiado e toque em **Publicar**.
6. **Configurações do projeto (engrenagem) → Seus apps → Web (`</>`)**: registre o app e copie `apiKey`, `authDomain`, `projectId` e `appId`.

## 2. Configurar

Abra `firebase-config.js` e troque os valores `COLE_AQUI` / `SEU-PROJETO` pelos dados do passo 6.

## 3. Subir pelo celular (GitHub → Netlify)

1. No github.com crie um repositório.
2. **Add file → Upload files** e envie `index.html`, `admin.html` e `firebase-config.js`.
3. Na Netlify: **Add new site → Import an existing project → GitHub**, escolha o repositório e toque em **Deploy** (sem comando de build).
4. No Firebase: **Authentication → Configurações → Domínios autorizados** e adicione `seusite.netlify.app`.

## 4. Usar

Abra `seusite.netlify.app/admin`, entre com o usuário (só SEUUSUARIO, sem o @painel.local) e a senha do passo 4 e cadastre categorias e grupos. Tudo aparece no site na hora, sem republicar.

## Observações

- Só o UID das regras consegue gravar. Qualquer pessoa pode abrir a tela de login, mas não consegue editar.
- As fotos ficam salvas dentro do banco (limite de cerca de 1 MB por grupo). O painel reduz as imagens ao enviar.
- Os contadores de visitas e acessos são públicos e podem ser inflados por quem quiser.
- Para atualizar o site depois, edite o arquivo no GitHub e a Netlify publica sozinha.
