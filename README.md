<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no" />
<title>DuoLogos - Curso Completo Grego Bíblico + Exercícios</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cardo&family=Inter&display=swap');
  :root {
    --bg:#1f1330; 
    --gold:#d4b24a; 
    --muted:#cfc4d0; 
    --card:#2b1f3a;
  }
  html, body {
    height:100%; margin:0; padding:0;
    font-family: 'Inter', system-ui, -apple-system, Roboto, 'Helvetica Neue', Arial, sans-serif;
    background: linear-gradient(180deg,#150a24 0%, #1f1330 100%);
    color: var(--muted);
    -webkit-font-smoothing: antialiased;
  }
  .app {
    max-width: 480px;
    margin: 0 auto;
    padding: 18px 16px 30px;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  header {
    display:flex; align-items:center; gap:12px;
    margin-bottom: 20px;
  }
  .logo {
    width:54px; height:54px; border-radius:12px;
    background: linear-gradient(135deg,var(--gold),#a7852d);
    display:flex; align-items:center; justify-content:center;
    color:#1f1330; font-weight:700; font-size: 24px;
    user-select:none;
  }
  h1 {
    margin:0; font-size: 20px;
  }
  nav {
    margin-bottom: 16px;
    display: flex; gap: 10px; justify-content:center; flex-wrap: wrap;
  }
  nav button {
    padding: 10px 14px;
    border-radius: 12px;
    border: none;
    background: var(--card);
    color: var(--muted);
    font-weight: 600;
    cursor: pointer;
    user-select:none;
    transition: background 0.3s;
    min-width: 110px;
    text-align:center;
  }
  nav button.active, nav button:hover {
    background: var(--gold);
    color: #1f1330;
    font-weight: 700;
  }
  main {
    background: var(--card);
    border-radius: 14px;
    padding: 18px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.45);
    flex-grow: 1;
    overflow-y: auto;
  }
  .greek-letter {
    font-family: 'Cardo', serif;
    font-size: 48px;
    font-weight: 700;
    color: var(--gold);
    text-align: center;
    user-select:none;
    margin-bottom: 12px;
  }
  .lesson-content {
    font-size: 18px;
    line-height: 1.4;
    user-select:none;
  }
  ul {
    padding-left: 18px;
  }
  li {
    margin-bottom: 6px;
  }
  /* Botões das opções */
  #exercise-write-options button, #exercise-translate-options button {
    background: var(--card);
    border: none;
    border-radius: 12px;
    color: var(--muted);
    padding: 12px 18px;
    flex: 1 1 40%;
    cursor: pointer;
    font-weight: 600;
    transition: background 0.3s;
    user-select:none;
  }
  #exercise-write-options button:hover, #exercise-translate-options button:hover {
    background: var(--gold);
    color: #1f1330;
  }
  #exercise-feedback, #translate-feedback {
    margin-top: 18px;
    font-weight: 700;
    text-align: center;
    user-select:none;
  }
  button.primary {
    margin-top: 18px;
    padding: 12px 22px;
    background: var(--gold);
    border: none;
    border-radius: 14px;
    font-weight: 700;
    color: #1f1330;
    cursor: pointer;
    user-select:none;
  }
  button.primary:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }
  label {
    display: block;
    margin-top: 14px;
    font-weight: 600;
  }
  input[type=text] {
    width: 100%;
    padding: 10px;
    border-radius: 12px;
    border: 1px solid rgba(255,255,255,0.15);
    background: transparent;
    color: var(--muted);
    font-size: 18px;
    box-sizing: border-box;
  }
  .hint {
    margin-top: 12px;
    font-size: 16px;
    color: #d4b24a;
    font-weight: 600;
    user-select:none;
  }
  /* Progress bar */
  .progress-text {
    margin-top: 16px; 
    text-align:center; 
    font-size:14px; 
    color:#aaa;
  }
  /* Scroll barras para mobile */
  main::-webkit-scrollbar {
    width: 8px;
  }
  main::-webkit-scrollbar-thumb {
    background: var(--gold);
    border-radius: 10px;
  }
  main::-webkit-scrollbar-track {
    background: transparent;
  }
  /* Responsividade */
  @media (max-width: 480px){
    #exercise-write-options button, #exercise-translate-options button {
      flex: 1 1 100%;
    }
    .app {
      padding: 14px 12px 24px;
    }
    h1 {
      font-size: 18px;
    }
    nav button {
      min-width: 90px;
      font-size: 14px;
    }
    .greek-letter {
      font-size: 38px;
    }
  }
</style>
</head>
<body>
  <div class="app" role="main">
    <header>
      <div class="logo" aria-hidden="true">DL</div>
      <h1>Curso Completo Grego Bíblico + Exercícios</h1>
    </header>

    <nav aria-label="Navegação do curso">
      <button id="btn-licoes" class="active" aria-current="page">Lições & Exercícios</button>
      <button id="btn-alfabeto">Alfabeto</button>
    </nav>

    <main id="lesson-container" tabindex="0" aria-live="polite" aria-atomic="true">
      <!-- Conteúdo carregado aqui -->
    </main>
  </div>

<script>
  // 24 letras do alfabeto, para referência em lições/exercícios
  const ALFABETO_COMPLETO = [
    {mai: 'Α', min: 'α', nome: 'Alfa'},
    {mai: 'Β', min: 'β', nome: 'Beta'},
    {mai: 'Γ', min: 'γ', nome: 'Gama'},
    {mai: 'Δ', min: 'δ', nome: 'Delta'},
    {mai: 'Ε', min: 'ε', nome: 'Epsilon'},
    {mai: 'Ζ', min: 'ζ', nome: 'Zeta'},
    {mai: 'Η', min: 'η', nome: 'Eta'},
    {mai: 'Θ', min: 'θ', nome: 'Teta'},
    {mai: 'Ι', min: 'ι', nome: 'Iota'},
    {mai: 'Κ', min: 'κ', nome: 'Kapa'},
    {mai: 'Λ', min: 'λ', nome: 'Lambda'},
    {mai: 'Μ', min: 'μ', nome: 'Mi'},
    {mai: 'Ν', min: 'ν', nome: 'Ni'},
    {mai: 'Ξ', min: 'ξ', nome: 'Xi'},
    {mai: 'Ο', min: 'ο', nome: 'Ómicron'},
    {mai: 'Π', min: 'π', nome: 'Pi'},
    {mai: 'Ρ', min: 'ρ', nome: 'Rô'},
    {mai: 'Σ', min: 'σ', nome: 'Sigma'},
    {mai: 'Τ', min: 'τ', nome: 'Tau'},
    {mai: 'Υ', min: 'υ', nome: 'Ípsilon'},
    {mai: 'Φ', min: 'φ', nome: 'Phi'},
    {mai: 'Χ', min: 'χ', nome: 'Chi'},
    {mai: 'Ψ', min: 'ψ', nome: 'Psi'},
    {mai: 'Ω', min: 'ω', nome: 'Ômega'}
  ];

  // 20 Lições com vocabulário e frases
  const LICOES = [
    {
      titulo: 'Lição 1: Introdução ao Alfabeto Grego',
      texto: `Aprenda as 24 letras do alfabeto grego, base fundamental para ler o Novo Testamento.`,
      palavras: ALFABETO_COMPLETO.map(l => ({grego: l.mai + ' / ' + l.min, pt: l.nome}))
    },
    {
      titulo: 'Lição 2: Palavras Essenciais I',
      texto: `Estude algumas palavras básicas muito usadas na Bíblia.`,
      palavras: [
        {grego: 'λόγος', pt: 'palavra, verbo'},
        {grego: 'θεός', pt: 'Deus'},
        {grego: 'ἀγάπη', pt: 'amor'},
        {grego: 'πίστις', pt: 'fé'}
      ]
    },
    {
      titulo: 'Lição 3: Palavras Essenciais II',
      texto: `Mais palavras importantes para seu vocabulário inicial.`,
      palavras: [
        {grego: 'χάρις', pt: 'graça'},
        {grego: 'ἄνθρωπος', pt: 'homem, ser humano'},
        {grego: 'ψυχή', pt: 'alma, vida'},
        {grego: 'Ἰησοῦς', pt: 'Jesus'}
      ]
    },
    {
      titulo: 'Lição 4: Frases Simples I',
      texto: `Vamos ler algumas frases curtas para começar a compreender frases.`,
      frases: [
        {grego: 'ὁ λόγος τοῦ θεοῦ', pt: 'a palavra de Deus'},
        {grego: 'ἀγάπη ἐστὶν ἀλήθεια', pt: 'amor é verdade'}
      ]
    },
    {
      titulo: 'Lição 5: Frases Simples II',
      texto: `Continuando com frases básicas importantes.`,
      frases: [
        {grego: 'πίστις καὶ χάρις', pt: 'fé e graça'},
        {grego: 'ψυχή ἀθάνατος', pt: 'alma imortal'}
      ]
    },
    {
      titulo: 'Lição 6: Verbos Comuns I',
      texto: `Verbos básicos e seus significados.`,
      palavras: [
        {grego: 'εἰμί', pt: 'ser, estar'},
        {grego: 'λέγω', pt: 'dizer, falar'},
        {grego: 'ἀκούω', pt: 'ouvir, escutar'}
      ]
    },
    {
      titulo: 'Lição 7: Verbos Comuns II',
      texto: `Mais verbos fundamentais.`,
      palavras: [
        {grego: 'βλέπω', pt: 'ver'},
        {grego: 'πείθω', pt: 'convencer, persuadir'},
        {grego: 'πορεύομαι', pt: 'ir, caminhar'}
      ]
    },
    {
      titulo: 'Lição 8: Substantivos Importantes',
      texto: `Substantivos muito usados no Grego Bíblico.`,
      palavras: [
        {grego: 'πατήρ', pt: 'pai'},
        {grego: 'μήτηρ', pt: 'mãe'},
        {grego: 'θελημα', pt: 'vontade'}
      ]
    },
    {
      titulo: 'Lição 9: Adjetivos',
      texto: `Adjetivos comuns para descrever pessoas e coisas.`,
      palavras: [
        {grego: 'καλός', pt: 'bom, belo'},
        {grego: 'ἅγιος', pt: 'santo'},
        {grego: 'μέγας', pt: 'grande'}
      ]
    },
    {
      titulo: 'Lição 10: Pronomes',
      texto: `Pronomes importantes para entender frases.`,
      palavras: [
        {grego: 'ἐγώ', pt: 'eu'},
        {grego: 'σύ', pt: 'tu, você'},
        {grego: 'αὐτός', pt: 'ele, ela, isso'}
      ]
    },
    {
      titulo: 'Lição 11: Preposições',
      texto: `Preposições básicas com exemplos.`,
      palavras: [
        {grego: 'ἐν', pt: 'em, dentro de'},
        {grego: 'εἰς', pt: 'para, até'},
        {grego: 'μετά', pt: 'com, depois'}
      ]
    },
    {
      titulo: 'Lição 12: Conjunções',
      texto: `Conjunções usadas para ligar frases.`,
      palavras: [
        {grego: 'καί', pt: 'e, também'},
        {grego: 'δέ', pt: 'mas, porém'},
        {grego: 'γάρ', pt: 'pois'}
      ]
    },
    {
      titulo: 'Lição 13: Números',
      texto: `Números básicos para compreensão.`,
      palavras: [
        {grego: 'εἷς', pt: 'um'},
        {grego: 'δύο', pt: 'dois'},
        {grego: 'τρεῖς', pt: 'três'}
      ]
    },
    {
      titulo: 'Lição 14: Expressões de Tempo',
      texto: `Expressões importantes para tempo e duração.`,
      palavras: [
        {grego: 'σήμερον', pt: 'hoje'},
        {grego: 'αὔριον', pt: 'amanhã'},
        {grego: 'χθές', pt: 'ontem'}
      ]
    },
    {
      titulo: 'Lição 15: Expressões de Lugar',
      texto: `Expressões que indicam lugar.`,
      palavras: [
        {grego: 'ὧδε', pt: 'aqui'},
        {grego: 'ἐκεῖ', pt: 'ali, lá'},
        {grego: 'πάντα', pt: 'todo lugar'}
      ]
    },
    {
      titulo: 'Lição 16: Verbos Irregulares',
      texto: `Verbos com conjugações irregulares comuns.`,
      palavras: [
        {grego: 'ἔρχομαι', pt: 'vir, ir'},
        {grego: 'φέρω', pt: 'trazer, carregar'},
        {grego: 'γίνομαι', pt: 'tornar-se, acontecer'}
      ]
    },
    {
      titulo: 'Lição 17: Palavras Relacionadas à Fé',
      texto: `Vocabulário que aparece frequentemente em contextos de fé.`,
      palavras: [
        {grego: 'πίστις', pt: 'fé'},
        {grego: 'ἐλπίς', pt: 'esperança'},
        {grego: 'ἀλήθεια', pt: 'verdade'}
      ]
    },
    {
      titulo: 'Lição 18: Palavras Relacionadas ao Amor',
      texto: `Termos usados para falar sobre amor e relacionamento.`,
      palavras: [
        {grego: 'ἀγάπη', pt: 'amor'},
        {grego: 'φιλία', pt: 'amizade, amor fraterno'},
        {grego: 'ἔρως', pt: 'amor romântico'}
      ]
    },
    {
      titulo: 'Lição 19: Frases Bíblicas Comuns',
      texto: `Frases que aparecem frequentemente no Novo Testamento.`,
      frases: [
        {grego: 'Εὐλογημένος ὁ ἐρχόμενος', pt: 'Bendito o que vem'},
        {grego: 'Ἀμήν λέγω ὑμῖν', pt: 'Em verdade vos digo'},
        {grego: 'Ὁ πατὴρ ἀγαπᾷ τὸν υἱόν', pt: 'O Pai ama o Filho'}
      ]
    },
    {
      titulo: 'Lição 20: Revisão Geral',
      texto: `Vamos revisar os principais conceitos e vocabulários estudados.`,
      palavras: ALFABETO_COMPLETO.slice(0,10).map(l => ({grego: l.mai + ' / ' + l.min, pt: l.nome}))
        .concat([
          {grego: 'λόγος', pt: 'palavra, verbo'},
          {grego: 'θεός', pt: 'Deus'},
          {grego: 'ἀγάπη', pt: 'amor'},
          {grego: 'πίστις', pt: 'fé'}
        ])
    }
  ];

  // Estado geral da aula e progresso
  let state = {
    currentTab: 'licoes',
    currentLesson: 0,
    currentExerciseType: 'write', // 'write' ou 'translate'
    writeIndex: 0,
    translateIndex: 0,
    // Salvaremos o progresso no localStorage
  };

  // Helpers para salvar/recuperar progresso
  function saveState(){
    localStorage.setItem('curso-grego-biblico-state', JSON.stringify(state));
  }
  function loadState(){
    const saved = localStorage.getItem('curso-grego-biblico-state');
    if(saved){
      try {
        const obj = JSON.parse(saved);
        if(typeof obj === 'object'){
          Object.assign(state, obj);
        }
      } catch(e){}
    }
  }

  // Renderiza o conteúdo da lição + exercícios combinados
  function renderLesson(){
    const lesson = LICOES[state.currentLesson];
    if(!lesson) return;

    const container = document.getElementById('lesson-container');

    // Conteúdo textual
    let conteudoHTML = `<h2>${lesson.titulo}</h2>`;
    conteudoHTML += `<p class="lesson-content">${lesson.texto}</p>`;

    // Mostrar vocabulário ou frases da lição
    if(lesson.palavras && lesson.palavras.length){
      conteudoHTML += `<h3>Vocabulário</h3><ul>`;
      lesson.palavras.forEach(p=>{
        conteudoHTML += `<li><strong>${p.grego}</strong> — ${p.pt}</li>`;
      });
      conteudoHTML += `</ul>`;
    }
    if(lesson.frases && lesson.frases.length){
      conteudoHTML += `<h3>Frases</h3><ul>`;
      lesson.frases.forEach(f=>{
        conteudoHTML += `<li><strong>${f.grego}</strong> — ${f.pt}</li>`;
      });
      conteudoHTML += `</ul>`;
    }

    // Exercício a mostrar depende do tipo atual
    let exercHTML = '';

    // Define o conjunto de palavras para exercícios
    let exercPalavras = [];
    if(lesson.palavras && lesson.palavras.length){
      exercPalavras = lesson.palavras;
    } else if(lesson.frases && lesson.frases.length){
      exercPalavras = lesson.frases;
    }

    if(exercPalavras.length === 0){
      exercHTML = `<p><em>Sem exercícios para esta lição.</em></p>`;
    } else if(state.currentExerciseType === 'write'){
      // Exercício de escrever palavra pelo grego (mostra palavra em português e pede escrever grego)
      const index = state.writeIndex % exercPalavras.length;
      const palavra = exercPalavras[index];
      exercHTML = `
        <h3>Exercício de escrita</h3>
        <p>Digite a palavra grega para: <strong>${palavra.pt}</strong></p>
        <input type="text" id="input-write" aria-label="Digite a palavra grega" autocomplete="off" autocapitalize="none" spellcheck="false" />
        <button id="btn-check-write" class="primary">Verificar</button>
        <button id="btn-hint-write" style="margin-top:10px; background: var(--gold); border:none; color:#1f1330; font-weight:700; border-radius:12px; padding: 8px 12px; cursor:pointer;">Mostrar dica</button>
        <div id="hint-write" class="hint" style="display:none;">${palavra.grego}</div>
        <div id="exercise-feedback" role="alert"></div>
        <div class="progress-text">Palavra ${index+1} de ${exercPalavras.length}</div>
      `;
    } else if(state.currentExerciseType === 'translate'){
      // Exercício de traduzir palavra (mostra palavra grega e pede tradução)
      const index = state.translateIndex % exercPalavras.length;
      const palavra = exercPalavras[index];
      exercHTML = `
        <h3>Exercício de tradução</h3>
        <p>Qual a tradução em português para: <strong>${palavra.grego}</strong>?</p>
        <input type="text" id="input-translate" aria-label="Digite a tradução em português" autocomplete="off" autocapitalize="sentences" spellcheck="false" />
        <button id="btn-check-translate" class="primary">Verificar</button>
        <button id="btn-hint-translate" style="margin-top:10px; background: var(--gold); border:none; color:#1f1330; font-weight:700; border-radius:12px; padding: 8px 12px; cursor:pointer;">Mostrar dica</button>
        <div id="hint-translate" class="hint" style="display:none;">Dica: ${palavra.pt}</div>
        <div id="translate-feedback" role="alert"></div>
        <div class="progress-text">Palavra ${index+1} de ${exercPalavras.length}</div>
      `;
    }

    // Botões de navegação e troca de exercício
    exercHTML += `
      <div style="margin-top: 20px; display:flex; justify-content: space-between; gap: 10px; flex-wrap: wrap;">
        <button id="btn-prev-lesson" ${state.currentLesson === 0 ? 'disabled' : ''}>Anterior</button>
        <button id="btn-toggle-exercise" style="flex-grow: 1;">Alternar Exercício (${state.currentExerciseType === 'write' ? 'Escrever' : 'Traduzir'})</button>
        <button id="btn-next-lesson" ${state.currentLesson === LICOES.length - 1 ? 'disabled' : ''}>Próxima</button>
      </div>
    `;

    container.innerHTML = conteudoHTML + exercHTML;
    container.focus();

    // Botões e eventos
    // Navegação lições
    document.getElementById('btn-prev-lesson').onclick = () => {
      if(state.currentLesson > 0){
        state.currentLesson--;
        state.writeIndex = 0;
        state.translateIndex = 0;
        saveState();
        renderLesson();
      }
    };
    document.getElementById('btn-next-lesson').onclick = () => {
      if(state.currentLesson < LICOES.length - 1){
        state.currentLesson++;
        state.writeIndex = 0;
        state.translateIndex = 0;
        saveState();
        renderLesson();
      }
    };
    // Alternar exercício
    document.getElementById('btn-toggle-exercise').onclick = () => {
      state.currentExerciseType = (state.currentExerciseType === 'write' ? 'translate' : 'write');
      saveState();
      renderLesson();
    };

    // Exercício escrever
    if(state.currentExerciseType === 'write'){
      const btnCheck = document.getElementById('btn-check-write');
      const btnHint = document.getElementById('btn-hint-write');
      const input = document.getElementById('input-write');
      const hintDiv = document.getElementById('hint-write');
      const feedback = document.getElementById('exercise-feedback');

      btnHint.onclick = () => {
        hintDiv.style.display = 'block';
      };
      btnCheck.onclick = () => {
        const val = input.value.trim();
        if(!val){
          feedback.textContent = 'Digite algo para verificar.';
          feedback.style.color = '#ff7b7b';
          return;
        }
        const correct = exercPalavras[state.writeIndex % exercPalavras.length].grego;
        if(val === correct){
          feedback.textContent = '✅ Correto!';
          feedback.style.color = '#8ef08e';
          state.writeIndex++;
          input.value = '';
          hintDiv.style.display = 'none';
        } else {
          feedback.textContent = `❌ Errado! A resposta correta é: ${correct}`;
          feedback.style.color = '#ff7b7b';
        }
        saveState();
        renderLesson();
      };
      input.addEventListener('keydown', e => {
        if(e.key === 'Enter'){
          btnCheck.click();
        }
      });
    }

    // Exercício traduzir
    if(state.currentExerciseType === 'translate'){
      const btnCheck = document.getElementById('btn-check-translate');
      const btnHint = document.getElementById('btn-hint-translate');
      const input = document.getElementById('input-translate');
      const hintDiv = document.getElementById('hint-translate');
      const feedback = document.getElementById('translate-feedback');

      btnHint.onclick = () => {
        hintDiv.style.display = 'block';
      };
      btnCheck.onclick = () => {
        const val = input.value.trim().toLowerCase();
        if(!val){
          feedback.textContent = 'Digite algo para verificar.';
          feedback.style.color = '#ff7b7b';
          return;
        }
        // aceita respostas próximas, split por vírgula ou ponto e vírgula
        const correto = exercPalavras[state.translateIndex % exercPalavras.length].pt.toLowerCase();
        const corretos = correto.split(/,|;/).map(s => s.trim());
        const acertou = corretos.some(c => val.includes(c));
        if(acertou){
          feedback.textContent = '✅ Correto!';
          feedback.style.color = '#8ef08e';
          state.translateIndex++;
          input.value = '';
          hintDiv.style.display = 'none';
        } else {
          feedback.textContent = `❌ Errado! A tradução correta é: ${correto}`;
          feedback.style.color = '#ff7b7b';
        }
        saveState();
        renderLesson();
      };
      input.addEventListener('keydown', e => {
        if(e.key === 'Enter'){
          btnCheck.click();
        }
      });
    }
  }

  // Renderiza o alfabeto completo numa aba separada
  function renderAlfabeto(){
    const container = document.getElementById('lesson-container');
    let html = `<h2>Alfabeto Grego Completo</h2><ul>`;
    ALFABETO_COMPLETO.forEach(l => {
      html += `<li><span class="greek-letter" aria-hidden="true" style="font-size:28px; margin-right:8px;">${l.mai} / ${l.min}</span><strong>${l.nome}</strong></li>`;
    });
    html += `</ul>`;
    container.innerHTML = html;
    container.focus();
  }

  // Controle das abas
  const btnLicoes = document.getElementById('btn-licoes');
  const btnAlfabeto = document.getElementById('btn-alfabeto');

  btnLicoes.onclick = () => {
    if(state.currentTab !== 'licoes'){
      state.currentTab = 'licoes';
      btnLicoes.classList.add('active');
      btnAlfabeto.classList.remove('active');
      saveState();
      renderLesson();
    }
  };
  btnAlfabeto.onclick = () => {
    if(state.currentTab !== 'alfabeto'){
      state.currentTab = 'alfabeto';
      btnAlfabeto.classList.add('active');
      btnLicoes.classList.remove('active');
      saveState();
      renderAlfabeto();
    }
  };

  // Inicializa o app
  function init(){
    loadState();
    if(state.currentTab === 'alfabeto'){
      btnAlfabeto.classList.add('active');
      btnLicoes.classList.remove('active');
      renderAlfabeto();
    } else {
      btnLicoes.classList.add('active');
      btnAlfabeto.classList.remove('active');
      renderLesson();
    }
  }
  init();
</script>

</body>
</html>
