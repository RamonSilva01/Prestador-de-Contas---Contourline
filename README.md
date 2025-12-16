# 📱 Prestador de Contas - Contourline

![Deploy Status](https://api.netlify.com/api/v1/badges/6924917ab1ab8c0072e16871/deploy-status)
![Tech](https://img.shields.io/badge/Stack-React_|_Tailwind_|_Supabase-blue)
![Type](https://img.shields.io/badge/Architecture-Single_File_SPA-orange)

> **Aplicação em Produção:** [Acessar Sistema Online](https://6924917ab1ab8c0072e16871--prestadordecontas.netlify.app/)

## 📄 Sobre o Projeto

Este repositório contém o código-fonte completo da aplicação de **Prestação de Contas** utilizada pela **Contourline Equipamentos Médicos e Diagnósticos**.

O projeto foi construído com uma arquitetura **Serverless & Standalone**: todo o motor da aplicação (React), estilização (Tailwind) e lógica de banco de dados (Supabase) residem em um único arquivo otimizado. Isso permite um *deploy* instantâneo e manutenção simplificada, sem dependência de ambientes de build complexos (como Webpack ou Node.js).

### 🚀 Funcionalidades em Produção

O sistema está ativo e operando com as seguintes capacidades:

* **⚡ Sincronização Real-time:** Conexão direta com banco de dados PostgreSQL (Supabase) para salvar despesas instantaneamente.
* **☁️ Gestão de Comprovantes:** Upload de fotos de notas fiscais direto para o Storage na nuvem.
* **📊 Relatórios Financeiros:** O sistema processa os dados no navegador e gera arquivos CSV (Excel) consolidados com um clique.
* **🔐 Autenticação:** Sistema de login e cadastro de usuários integrado.

---

## 🛠 Tecnologias

A aplicação roda inteiramente no lado do cliente (Client-Side), consumindo APIs externas:

* **Frontend:** React 18 (Babel Standalone)
* **UI/UX:** Tailwind CSS (via CDN)
* **Backend:** Supabase (Database & Auth)
* **Hospedagem:** Netlify

---

## 💻 Estrutura do Código

Como a aplicação é *Standalone*, a estrutura de arquivos é intencionalmente simples:

```text
/
├── index.html                       <-- O App Completo (Lógica + UI)
├── Logotipo-Contourline Branca.png  <-- Assets visuais
└── README.md                        <-- Documentação
Destaque da Implementação (React Standalone)
O código abaixo ilustra como o React é inicializado diretamente no navegador sem build steps, permitindo a renderização da interface e conexão com o Supabase no mesmo script:

JavaScript

// Exemplo da inicialização direta no index.html
const App = () => {
    const [expenses, setExpenses] = React.useState([]);
    
    // Conexão direta com Supabase sem backend intermediário
    React.useEffect(() => {
        const initSupabase = async () => {
            supabaseClient = window.supabase.createClient(URL, KEY);
            // ... lógica de auth
        };
        initSupabase();
    }, []);
    
    return (
        <div className="min-h-screen bg-gray-50">
           {/* Componentes da UI */}
        </div>
    );
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
🔄 Como fazer o Deploy
Para atualizar a versão que está no ar:

Edite o arquivo index.html.

Faça o commit no GitHub.

O Netlify (conectado a este repositório) detectará a mudança e atualizará o site automaticamente em segundos.

⚠️ Nota de Segurança
As chaves de API do Supabase (SUPABASE_URL e SUPABASE_KEY) utilizadas neste projeto estão configuradas com Row Level Security (RLS), garantindo que usuários só possam acessar e modificar seus próprios dados, mesmo com as chaves visíveis no código do cliente.

Desenvolvido por Ramon Silva
