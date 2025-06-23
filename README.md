<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Assistenti Sociali - Prepariamoci Pupa</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 400px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
            position: relative;
        }

        .header {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 30px 20px;
            text-align: center;
            position: relative;
        }

        .header h1 {
            font-size: 24px;
            margin-bottom: 10px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }

        .header p {
            font-size: 14px;
            opacity: 0.9;
        }

        .content {
            padding: 30px 20px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .btn {
            width: 100%;
            padding: 18px;
            border: none;
            border-radius: 15px;
            font-size: 18px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            margin-bottom: 15px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .btn-primary {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .btn-secondary {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        .btn-danger {
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
        }

        .btn-warning {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            color: #333;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
        }

        .subject-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }

        .subject-btn {
            padding: 20px 10px;
            border: none;
            border-radius: 15px;
            font-size: 14px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            text-align: center;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .subject-btn:hover {
            transform: translateY(-2px);
        }

        .subject-servizio { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
        .subject-etica { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); }
        .subject-penitenziario { background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); }
        .subject-penale { background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%); }
        .subject-amministrativo { background: linear-gradient(135deg, #fa709a 0%, #fee140 100%); }

        .quiz-container {
            text-align: center;
        }

        .question-counter {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            font-weight: bold;
        }

        .question {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .question h3 {
            color: #333;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        .answers {
            display: grid;
            gap: 10px;
        }

        .answer-btn {
            padding: 15px;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            background: white;
            color: #333;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: left;
            font-size: 14px;
        }

        .answer-btn:hover {
            border-color: #667eea;
            background: #f8f9ff;
        }

        .answer-btn.correct {
            background: #d4edda;
            border-color: #28a745;
            color: #155724;
        }

        .answer-btn.incorrect {
            background: #f8d7da;
            border-color: #dc3545;
            color: #721c24;
        }

        .timer {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
            color: #333;
        }

        .settings {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .checkbox-container {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }

        .results {
            text-align: center;
            padding: 20px;
        }

        .score {
            font-size: 48px;
            margin: 20px 0;
        }

        .score.good { color: #28a745; }
        .score.average { color: #ffc107; }
        .score.poor { color: #dc3545; }

        .back-btn {
            background: #6c757d;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            margin-bottom: 20px;
        }

        .study-mode {
            background: #e7f3ff;
            border-left: 4px solid #007bff;
            padding: 15px;
            margin: 10px 0;
            border-radius: 5px;
        }

        @media (max-width: 480px) {
            .container {
                margin: 10px;
                max-width: none;
            }
            
            .subject-grid {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📚 Quiz Assistenti Sociali</h1>
            <p>Prepariamoci insieme per il concorso! 💪</p>
        </div>

        <div class="content">
            <!-- Pagina principale -->
            <div class="page active" id="home">
                <button class="btn btn-primary" onclick="showPage('menu')">
                    🚀 Prepariamoci Pupa!
                </button>
            </div>

            <!-- Menu principale -->
            <div class="page" id="menu">
                <button class="back-btn" onclick="showPage('home')">← Indietro</button>
                <button class="btn btn-secondary" onclick="showPage('quiz-settings')">
                    🎯 Quiz Completo
                </button>
                <button class="btn btn-danger" onclick="showPage('subjects')">
                    📖 Quiz per Materia
                </button>
                <button class="btn btn-warning" onclick="showStudyMode()">
                    🔍 Modalità Studio
                </button>
            </div>

            <!-- Selezione materie -->
            <div class="page" id="subjects">
                <button class="back-btn" onclick="showPage('menu')">← Indietro</button>
                <h2 style="text-align: center; margin-bottom: 20px; color: #333;">Scegli la Materia</h2>
                <div class="subject-grid">
                    <button class="subject-btn subject-servizio" onclick="startQuiz('servizio')">
                        🤝<br>Servizio Sociale
                    </button>
                    <button class="subject-btn subject-etica" onclick="startQuiz('etica')">
                        ⚖️<br>Etica e Deontologia
                    </button>
                    <button class="subject-btn subject-penitenziario" onclick="startQuiz('penitenziario')">
                        🏛️<br>Diritto Penitenziario
                    </button>
                    <button class="subject-btn subject-penale" onclick="startQuiz('penale')">
                        👨‍⚖️<br>Diritto Penale
                    </button>
                    <button class="subject-btn subject-amministrativo" onclick="startQuiz('amministrativo')">
                        📋<br>Diritto Amministrativo
                    </button>
                </div>
            </div>

            <!-- Impostazioni quiz -->
            <div class="page" id="quiz-settings">
                <button class="back-btn" onclick="showPage('menu')">← Indietro</button>
                <h2 style="text-align: center; margin-bottom: 20px; color: #333;">Impostazioni Quiz</h2>
                <div class="settings">
                    <div class="checkbox-container">
                        <input type="checkbox" id="timer-enabled" checked>
                        <label for="timer-enabled">⏰ Abilita cronometro (45 minuti)</label>
                    </div>
                </div>
                <button class="btn btn-primary" onclick="startQuiz('completo')">
                    🎯 Inizia Quiz Completo
                </button>
            </div>

            <!-- Quiz -->
            <div class="page" id="quiz">
                <button class="back-btn" onclick="showPage('menu')">← Indietro</button>
                <div class="timer" id="timer" style="display: none;">
                    ⏰ Tempo rimasto: <span id="time-display">45:00</span>
                </div>
                <div class="question-counter">
                    Domanda <span id="current-question">1</span> di <span id="total-questions">30</span>
                </div>
                <div class="quiz-container">
                    <div class="question">
                        <h3 id="question-text"></h3>
                        <div class="answers" id="answers"></div>
                    </div>
                    <button class="btn btn-primary" id="next-btn" onclick="nextQuestion()" style="display: none;">
                        Prossima Domanda →
                    </button>
                </div>
            </div>

            <!-- Risultati -->
            <div class="page" id="results">
                <div class="results">
                    <h2>🎉 Quiz Completato!</h2>
                    <div class="score" id="score-display"></div>
                    <div id="score-text"></div>
                    <div id="score-emoji"></div>
                    <button class="btn btn-primary" onclick="showPage('menu')">
                        🏠 Torna al Menu
                    </button>
                    <button class="btn btn-secondary" onclick="showStudyMode()" id="study-wrong-btn" style="display: none;">
                        🔍 Studia Risposte Sbagliate
                    </button>
                </div>
            </div>

            <!-- Modalità studio -->
            <div class="page" id="study">
                <button class="back-btn" onclick="showPage('menu')">← Indietro</button>
                <h2 style="text-align: center; margin-bottom: 20px; color: #333;">📚 Modalità Studio</h2>
                <div id="study-content"></div>
            </div>
        </div>
    </div>

    <script>
        // Database delle domande
        const questionsDB = {
            servizio: [
                {
                    question: "Usufruendo della supervisione, l'assistente sociale:",
                    correct: "Può stabilire una distanza equilibrata dall'azione professionale.",
                    options: [
                        "Può stabilire una distanza equilibrata dall'azione professionale.",
                        "Deve sempre seguire le direttive del supervisore senza eccezioni.",
                        "Non può prendere decisioni autonome sui casi.",
                        "Deve riferire ogni dettaglio dei colloqui con gli utenti."
                    ]
                },
                {
                    question: "Come si chiama la modalità operativa specifica dell'assistente sociale?",
                    correct: "Processo d'aiuto.",
                    options: [
                        "Processo d'aiuto.",
                        "Processo di cura.",
                        "Processo di assistenza.",
                        "Processo di supporto."
                    ]
                },
                {
                    question: "È obiettivo del servizio sociale:",
                    correct: "Contribuire a migliorare i servizi per la salvaguardia e la tutela dei diritti della persona.",
                    options: [
                        "Contribuire a migliorare i servizi per la salvaguardia e la tutela dei diritti della persona.",
                        "Fornire esclusivamente assistenza economica ai bisognosi.",
                        "Sostituirsi alle famiglie nella cura dei minori.",
                        "Controllare e sanzionare i comportamenti socialmente inadeguati."
                    ]
                },
                {
                    question: "Nel Servizio Sociale la responsabilizzazione del soggetto:",
                    correct: "È uno degli obiettivi principali dell'intervento.",
                    options: [
                        "È uno degli obiettivi principali dell'intervento.",
                        "Non è mai perseguibile nei casi gravi.",
                        "È secondaria rispetto all'assistenza materiale.",
                        "È possibile solo con utenti collaborativi."
                    ]
                },
                {
                    question: "Il case work:",
                    correct: "Concentra la sua attenzione sull'individuo che chiede aiuto.",
                    options: [
                        "Concentra la sua attenzione sull'individuo che chiede aiuto.",
                        "Si occupa esclusivamente di casi familiari.",
                        "È un metodo superato nel servizio sociale moderno.",
                        "Si applica solo nei servizi sanitari."
                    ]
                },
                {
                    question: "L'indagine domiciliare:",
                    correct: "È uno strumento professionale da attuarsi a domicilio dell'utente attraverso l'osservazione dell'ambiente di vita e il colloquio.",
                    options: [
                        "È uno strumento professionale da attuarsi a domicilio dell'utente attraverso l'osservazione dell'ambiente di vita e il colloquio.",
                        "È sempre obbligatoria in ogni presa in carico.",
                        "Può essere effettuata senza il consenso dell'utente.",
                        "È di competenza esclusiva delle forze dell'ordine."
                    ]
                },
                {
                    question: "L'obiettivo del Servizio Sociale è:",
                    correct: "La tutela della persona nella sua esigenza di autodeterminarsi, in armonia con l'ambiente circostante.",
                    options: [
                        "La tutela della persona nella sua esigenza di autodeterminarsi, in armonia con l'ambiente circostante.",
                        "Il controllo sociale dei comportamenti devianti.",
                        "La redistribuzione delle risorse economiche.",
                        "L'integrazione forzata degli emarginati nella società."
                    ]
                },
                {
                    question: "La relazione scritta di servizio sociale:",
                    correct: "È un tipo di documentazione redatta dall'assistente sociale destinata a un referente esterno al servizio.",
                    options: [
                        "È un tipo di documentazione redatta dall'assistente sociale destinata a un referente esterno al servizio.",
                        "È sempre pubblica e accessibile a chiunque.",
                        "Non richiede autorizzazione dell'utente.",
                        "È obbligatoria solo nei casi giudiziari."
                    ]
                },
                {
                    question: "Il colloquio di servizio sociale:",
                    correct: "Non può essere stereotipato o, in senso stretto, direttivo, ma deve essere centrato sulla persona.",
                    options: [
                        "Non può essere stereotipato o, in senso stretto, direttivo, ma deve essere centrato sulla persona.",
                        "Deve sempre seguire un protocollo rigido e standardizzato.",
                        "È efficace solo se condotto in modo direttivo.",
                        "Non richiede particolare preparazione professionale."
                    ]
                },
                {
                    question: "La 'presa in carico' professionale comporta un approccio:",
                    correct: "Globale ed unitario ai bisogni della persona.",
                    options: [
                        "Globale ed unitario ai bisogni della persona.",
                        "Settoriale e specialistico per ogni problema.",
                        "Temporaneo e limitato nel tempo.",
                        "Standardizzato per tutti gli utenti."
                    ]
                }
            ],
            etica: [
                {
                    question: "Secondo quanto prevede il Codice deontologico, l'assistente sociale nel rapporto con enti, colleghi ed altri professionisti:",
                    correct: "Fornisce unicamente dati e informazioni strettamente attinenti e indispensabili alla definizione dell'intervento.",
                    options: [
                        "Fornisce unicamente dati e informazioni strettamente attinenti e indispensabili alla definizione dell'intervento.",
                        "Può condividere liberamente tutte le informazioni in suo possesso.",
                        "Deve riferire ogni dettaglio dei casi seguiti.",
                        "Non può collaborare con altri professionisti."
                    ]
                },
                {
                    question: "Prevede il Codice deontologico che l'assistente sociale, nel rapporto professionale:",
                    correct: "Non deve utilizzare la relazione con utenti e clienti per interessi o vantaggi personali.",
                    options: [
                        "Non deve utilizzare la relazione con utenti e clienti per interessi o vantaggi personali.",
                        "Può accettare regali di modico valore dagli utenti.",
                        "Può instaurare relazioni personali con gli utenti.",
                        "Può utilizzare le informazioni acquisite per fini personali."
                    ]
                },
                {
                    question: "La riservatezza ed il segreto professionale costituiscono:",
                    correct: "Diritto primario dell'utente e dovere dell'assistente sociale.",
                    options: [
                        "Diritto primario dell'utente e dovere dell'assistente sociale.",
                        "Una facoltà discrezionale dell'assistente sociale.",
                        "Un obbligo solo nei casi giudiziari.",
                        "Una prassi consigliata ma non obbligatoria."
                    ]
                },
                {
                    question: "L'assistente sociale è obbligato a deporre su quanto gli è stato confidato o ha conosciuto nell'esercizio della professione?",
                    correct: "No, salvo i casi previsti dalla legge.",
                    options: [
                        "No, salvo i casi previsti dalla legge.",
                        "Sì, sempre e in ogni circostanza.",
                        "Solo se lo ritiene opportuno per l'utente.",
                        "Solo su richiesta dell'autorità giudiziaria."
                    ]
                },
                {
                    question: "L'assistente sociale:",
                    correct: "Deve impegnare la sua competenza professionale per promuovere la piena autodeterminazione degli utenti.",
                    options: [
                        "Deve impegnare la sua competenza professionale per promuovere la piena autodeterminazione degli utenti.",
                        "Deve sempre decidere per conto degli utenti incapaci.",
                        "Non deve influenzare le decisioni degli utenti.",
                        "Può sostituirsi agli utenti nelle scelte importanti."
                    ]
                },
                {
                    question: "L'obiezione di coscienza è:",
                    correct: "Un diritto soggettivo.",
                    options: [
                        "Un diritto soggettivo.",
                        "Un dovere professionale.",
                        "Una facoltà discrezionale.",
                        "Un impedimento all'esercizio professionale."
                    ]
                },
                {
                    question: "Per esercitare la professione di assistente sociale, oltre al titolo accademico è necessario:",
                    correct: "Aver conseguito l'abilitazione mediante Esami di Stato ed essere iscritto all'albo professionale.",
                    options: [
                        "Aver conseguito l'abilitazione mediante Esami di Stato ed essere iscritto all'albo professionale.",
                        "Solo il titolo accademico è sufficiente.",
                        "Un tirocinio di almeno due anni.",
                        "Un corso di specializzazione post-laurea."
                    ]
                },
                {
                    question: "La professione dell'assistente sociale è caratterizzata da:",
                    correct: "Corpus teorico, legittimazione sociale, codice deontologico.",
                    options: [
                        "Corpus teorico, legittimazione sociale, codice deontologico.",
                        "Solo competenze pratiche acquisite sul campo.",
                        "Esclusivamente normative legislative.",
                        "Unicamente esperienza professionale."
                    ]
                },
                {
                    question: "L'assistente sociale dipendente di una pubblica amministrazione è tenuto ad osservare:",
                    correct: "Il segreto d'ufficio e il segreto professionale.",
                    options: [
                        "Il segreto d'ufficio e il segreto professionale.",
                        "Solo il segreto d'ufficio.",
                        "Solo il segreto professionale.",
                        "Nessun obbligo particolare di riservatezza."
                    ]
                },
                {
                    question: "La relazione tra assistente sociale e utente è:",
                    correct: "Professionale.",
                    options: [
                        "Professionale.",
                        "Personale e amichevole.",
                        "Puramente burocratica.",
                        "Di tipo familiare."
                    ]
                }
            ],
            penitenziario: [
                {
                    question: "Il regime di semilibertà:",
                    correct: "Consiste nella concessione al condannato e all'internato di trascorrere parte del giorno fuori dell'istituto per partecipare ad attività lavorative, istruttive o comunque utili al reinserimento sociale.",
                    options: [
                        "Consiste nella concessione al condannato e all'internato di trascorrere parte del giorno fuori dell'istituto per partecipare ad attività lavorative, istruttive o comunque utili al reinserimento sociale.",
                        "Permette di uscire solo per motivi di salute.",
                        "È applicabile solo ai detenuti con pena residua inferiore a un anno.",
                        "Richiede il consenso della vittima del reato."
                    ]
                },
                {
                    question: "Nel caso di recidiva, il condannato per essere ammesso alla liberazione condizionale, deve avere scontato:",
                    correct: "Almeno quattro anni di pena e non meno di tre quarti della pena inflittagli.",
                    options: [
                        "Almeno quattro anni di pena e non meno di tre quarti della pena inflittagli.",
                        "La metà della pena inflittagli.",
                        "Almeno due anni di pena.",
                        "L'intera pena senza possibilità di liberazione condizionale."
                    ]
                },
                {
                    question: "La liberazione anticipata:",
                    correct: "Deve essere concessa al condannato a pena detentiva che ha dato prova di partecipazione all'opera di rieducazione.",
                    options: [
                        "Deve essere concessa al condannato a pena detentiva che ha dato prova di partecipazione all'opera di rieducazione.",
                        "È automatica per tutti i detenuti.",
                        "Dipende esclusivamente dalla durata della pena.",
                        "È a discrezione del direttore dell'istituto."
                    ]
                },
                {
                    question: "Per i minorenni la liberazione condizionale:",
                    correct: "Può essere concessa indipendentemente dalla durata della pena.",
                    options: [
                        "Può essere concessa indipendentemente dalla durata della pena.",
                        "Segue le stesse regole degli adulti.",
                        "Non è mai applicabile.",
                        "Richiede sempre il consenso dei genitori."
                    ]
                },
                {
                    question: "I membri del Parlamento devono munirsi di autorizzazione per visitare un istituto penitenziario?",
                    correct: "No.",
                    options: [
                        "No.",
                        "Sì, sempre.",
                        "Solo per visite non ufficiali.",
                        "Solo se accompagnati da giornalisti."
                    ]
                },
                {
                    question: "Chi autorizza i ministri del culto cattolico, diversi dai cappellani, ad accedere nell'istituto?",
                    correct: "Il direttore dell'istituto.",
                    options: [
                        "Il direttore dell'istituto.",
                        "Il magistrato di sorveglianza.",
                        "Il Ministro della Giustizia.",
                        "Il tribunale di sorveglianza."
                    ]
                },
                {
                    question: "La detenzione domiciliare può essere applicata per l'espiazione della pena detentiva inflitta in misura non superiore a due anni?",
                    correct: "Sì, quando non ricorrono i presupposti per l'affidamento in prova al servizio sociale e sempre che tale misura sia idonea ad evitare il pericolo che il condannato commetta altri reati.",
                    options: [
                        "Sì, quando non ricorrono i presupposti per l'affidamento in prova al servizio sociale e sempre che tale misura sia idonea ad evitare il pericolo che il condannato commetta altri reati.",
                        "No, mai.",
                        "Solo per reati non gravi.",
                        "Solo per motivi di salute."
                    ]
                },
                {
                    question: "Da chi è presieduto il Consiglio di disciplina?",
                    correct: "Dal direttore dell'istituto.",
                    options: [
                        "Dal direttore dell'istituto.",
                        "Dal magistrato di sorveglianza.",
                        "Dal comandante della polizia penitenziaria.",
                        "Da un rappresentante dei detenuti."
                    ]
                },
                {
                    question: "Gli Uffici di Servizio Sociale per i minorenni (USSM) intervengono:",
                    correct: "In ogni stato e grado del procedimento penale.",
                    options: [
                        "In ogni stato e grado del procedimento penale.",
                        "Solo dopo la condanna definitiva.",
                        "Solo su richiesta del giudice.",
                        "Solo per reati gravi."
                    ]
                },
                {
                    question: "I condannati e gli internati che usufruiscono della semilibertà possono indossare abiti civili?",
                    correct: "Sì, dispone l'art. 48 dell'O.P. che i condannati e gli internati che usufruiscono della semilibertà indossano abiti civili.",
                    options: [
                        "Sì, dispone l'art. 48 dell'O.P. che i condannati e gli internati che usufruiscono della semilibertà indossano abiti civili.",
                        "No, devono sempre indossare la divisa carceraria.",
                        "Solo durante le ore di lavoro all'esterno.",
                        "Solo con autorizzazione speciale del direttore."
                    ]
                }
            ],
            penale: [
                {
                    question: "Quale delle seguenti pene principali previste dal codice penale si estende da 15 giorni a 24 anni?",
                    correct: "Reclusione.",
                    options: [
                        "Reclusione.",
                        "Arresto.",
                        "Multa.",
                        "Ammenda."
                    ]
                },
                {
                    question: "La pena dell'arresto si estende:",
                    correct: "Da cinque giorni a tre anni.",
                    options: [
                        "Da cinque giorni a tre anni.",
                        "Da quindici giorni a cinque anni.",
                        "Da un mese a due anni.",
                        "Da dieci giorni a quattro anni."
                    ]
                },
                {
                    question: "Il Giudice penale quando difetta la punibilità dell'imputato:",
                    correct: "Pronuncia sentenza di assoluzione.",
                    options: [
                        "Pronuncia sentenza di assoluzione.",
                        "Pronuncia sentenza di condanna con pena sospesa.",
                        "Rinvia il processo.",
                        "Dichiara il non luogo a procedere."
                    ]
                },
                {
                    question: "Quale tra le seguenti è una competenza del tribunale per i minorenni?",
                    correct: "Adozioni internazionali (art. 29 e ss. l. 184/1983).",
                    options: [
                        "Adozioni internazionali (art. 29 e ss. l. 184/1983).",
                        "Tutti i reati commessi da maggiorenni.",
                        "Controversie di lavoro.",
                        "Separazioni e divorzi."
                    ]
                },
                {
                    question: "La pena della multa:",
                    correct: "È sempre inflitta dal giudice con sentenza di condanna.",
                    options: [
                        "È sempre inflitta dal giudice con sentenza di condanna.",
                        "Può essere inflitta anche dall'autorità amministrativa.",
                        "È automatica per alcuni reati.",
                        "Può essere sostituita con lavori socialmente utili."
                    ]
                },
                {
                    question: "La richiesta di giudizio immediato è atto tipico che attribuisce alla persona che ne è oggetto la qualità di:",
                    correct: "Imputato.",
                    options: [
                        "Imputato.",
                        "Indagato.",
                        "Sospettato.",
                        "Persona informata sui fatti."
                    ]
                },
                {
                    question: "Il condannato all'ergastolo:",
                    correct: "È in stato di interdizione legale.",
                    options: [
                        "È in stato di interdizione legale.",
                        "Mantiene tutti i diritti civili.",
                        "Può amministrare liberamente i suoi beni.",
                        "Può esercitare il diritto di voto."
                    ]
                },
                {
                    question: "L'istituto dell'indulto:",
                    correct: "Consiste nel condono in tutto o in parte della pena principale ovvero nella sua commutazione in una pena di specie diversa ma dello stesso genere.",
                    options: [
                        "Consiste nel condono in tutto o in parte della pena principale ovvero nella sua commutazione in una pena di specie diversa ma dello stesso genere.",
                        "Cancella il reato dal casellario giudiziale.",
                        "È di competenza del giudice dell'esecuzione.",
                        "Si applica solo alle pene accessorie."
                    ]
                },
                {
                    question: "Nell'attuale sistema accusatorio il Giudice è:",
                    correct: "Titolare del potere decisionale.",
                    options: [
                        "Titolare del potere decisionale.",
                        "Responsabile delle indagini preliminari.",
                        "Parte del processo.",
                        "Consulente delle parti."
                    ]
                },
                {
                    question: "Con la maggiore età si acquista:",
                    correct: "La capacità giuridica.",
                    options: [
                        "La capacità di agire.",
                        "La capacità giuridica.",
                        "L'imputabilità penale.",
                        "La responsabilità civile."
                    ]
                }
            ],
            amministrativo: [
                {
                    question: "Per quanto riguarda il contenuto della motivazione dei provvedimenti amministrativi l'art. 3 della l. n. 241/1990 stabilisce che la motivazione deve indicare:",
                    correct: "I presupposti di fatto e le ragioni giuridiche che hanno determinato la decisione dell'amministrazione, in relazione alle risultanze dell'istruttoria.",
                    options: [
                        "I presupposti di fatto e le ragioni giuridiche che hanno determinato la decisione dell'amministrazione, in relazione alle risultanze dell'istruttoria.",
                        "Solo i riferimenti normativi applicati.",
                        "Esclusivamente i fatti accertati.",
                        "Unicamente la volontà dell'amministrazione."
                    ]
                },
                {
                    question: "Il provvedimento amministrativo adottato in violazione o elusione del giudicato:",
                    correct: "È nullo.",
                    options: [
                        "È nullo.",
                        "È annullabile.",
                        "È irregolare.",
                        "È pienamente valido."
                    ]
                },
                {
                    question: "I regolamenti dell'Esecutivo:",
                    correct: "Non possono regolare istituti fondamentali dell'ordinamento.",
                    options: [
                        "Non possono regolare istituti fondamentali dell'ordinamento.",
                        "Possono derogare alle leggi ordinarie.",
                        "Hanno la stessa forza delle leggi.",
                        "Possono modificare la Costituzione."
                    ]
                },
                {
                    question: "Con riferimento alle norme sul procedimento amministrativo chi valuta, ai fini istruttori, le condizioni di ammissibilità, i requisiti di legittimazione ed i presupposti?",
                    correct: "Il responsabile del procedimento.",
                    options: [
                        "Il responsabile del procedimento.",
                        "Il dirigente dell'ufficio.",
                        "Il segretario comunale.",
                        "Il sindaco o il presidente della giunta regionale."
                    ]
                },
                {
                    question: "La delega (o delegazione):",
                    correct: "È un meccanismo attraverso il quale un soggetto, titolare di un determinato potere, attribuisce mediante un proprio atto, l'esercizio dello stesso potere o di una parte ad altro soggetto.",
                    options: [
                        "È un meccanismo attraverso il quale un soggetto, titolare di un determinato potere, attribuisce mediante un proprio atto, l'esercizio dello stesso potere o di una parte ad altro soggetto.",
                        "È il trasferimento definitivo di competenze.",
                        "È una forma di sostituzione automatica.",
                        "È un atto di natura contrattuale."
                    ]
                },
                {
                    question: "Quanto ai criteri generali dell'azione amministrativa, quale tra quelli indicati è strettamente connesso al diritto di accesso?",
                    correct: "Trasparenza.",
                    options: [
                        "Trasparenza.",
                        "Efficacia.",
                        "Economicità.",
                        "Imparzialità."
                    ]
                },
                {
                    question: "Il termine del provvedimento amministrativo:",
                    correct: "È elemento accidentale che sottopone l'efficacia dell'atto o alcuni effetti al verificarsi di un evento futuro e certo.",
                    options: [
                        "È elemento accidentale che sottopone l'efficacia dell'atto o alcuni effetti al verificarsi di un evento futuro e certo.",
                        "È sempre elemento essenziale dell'atto.",
                        "Non può mai essere apposto.",
                        "È elemento naturale di ogni provvedimento."
                    ]
                },
                {
                    question: "L'agente del provvedimento amministrativo:",
                    correct: "Può essere un'autorità amministrativa, un privato esercente una pubblica funzione, ovvero un privato obbligato a svolgere un procedimento di evidenza pubblica.",
                    options: [
                        "Può essere un'autorità amministrativa, un privato esercente una pubblica funzione, ovvero un privato obbligato a svolgere un procedimento di evidenza pubblica.",
                        "È sempre un organo pubblico.",
                        "Non può mai essere un soggetto privato.",
                        "È esclusivamente il funzionario competente."
                    ]
                },
                {
                    question: "Il provvedimento amministrativo adottato in violazione di legge:",
                    correct: "È annullabile.",
                    options: [
                        "È annullabile.",
                        "È nullo.",
                        "È irregolare.",
                        "È sempre valido."
                    ]
                },
                {
                    question: "Il comando è:",
                    correct: "Un provvedimento mediante il quale la P.A., a seguito di una scelta discrezionale o di un accertamento, fa sorgere nuovi obblighi giuridici a carico dei destinatari.",
                    options: [
                        "Un provvedimento mediante il quale la P.A., a seguito di una scelta discrezionale o di un accertamento, fa sorgere nuovi obblighi giuridici a carico dei destinatari.",
                        "Un atto di natura contrattuale.",
                        "Una comunicazione informativa.",
                        "Un atto privo di efficacia giuridica."
                    ]
                }
            ]
        };

        // Variabili globali
        let currentQuiz = [];
        let currentQuestionIndex = 0;
        let score = 0;
        let wrongAnswers = [];
        let timer = null;
        let timeLeft = 2700; // 45 minuti in secondi
        let quizType = '';

        // Funzioni di navigazione
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
        }

        // Genera risposte alternative casuali
        function generateWrongAnswers(correct, subject) {
            const allAnswers = [];
            Object.values(questionsDB[subject]).forEach(q => {
                if (q.correct !== correct && !allAnswers.includes(q.correct)) {
                    allAnswers.push(q.correct);
                }
            });
            
            // Se non ci sono abbastanza risposte dalla stessa materia, aggiungi da altre materie
            if (allAnswers.length < 3) {
                Object.keys(questionsDB).forEach(subj => {
                    if (subj !== subject) {
                        Object.values(questionsDB[subj]).forEach(q => {
                            if (!allAnswers.includes(q.correct) && q.correct !== correct) {
                                allAnswers.push(q.correct);
                            }
                        });
                    }
                });
            }
            
            // Prendi 3 risposte casuali
            const shuffled = allAnswers.sort(() => 0.5 - Math.random());
            return shuffled.slice(0, 3);
        }

        // Prepara le domande per il quiz
        function prepareQuestions(subject) {
            let questions = [];
            
            if (subject === 'completo') {
                // Quiz completo: 6 domande per materia
                Object.keys(questionsDB).forEach(subj => {
                    const subjectQuestions = questionsDB[subj].sort(() => 0.5 - Math.random()).slice(0, 6);
                    questions.push(...subjectQuestions.map(q => ({...q, subject: subj})));
                });
            } else {
                // Quiz per materia specifica
                questions = questionsDB[subject].sort(() => 0.5 - Math.random()).slice(0, 30);
                questions = questions.map(q => ({...q, subject: subject}));
            }
            
            // Mescola le domande
            questions = questions.sort(() => 0.5 - Math.random());
            
            // Genera opzioni per ogni domanda
            return questions.map(q => {
                if (!q.options) {
                    const wrongAnswers = generateWrongAnswers(q.correct, q.subject);
                    const allOptions = [q.correct, ...wrongAnswers].sort(() => 0.5 - Math.random());
                    return {...q, options: allOptions};
                }
                return q;
            });
        }

        // Inizia il quiz
        function startQuiz(subject) {
            quizType = subject;
            currentQuiz = prepareQuestions(subject);
            currentQuestionIndex = 0;
            score = 0;
            wrongAnswers = [];
            
            // Gestione timer
            const timerEnabled = document.getElementById('timer-enabled').checked;
            if (timerEnabled) {
                timeLeft = 2700; // 45 minuti
                startTimer();
                document.getElementById('timer').style.display = 'block';
            } else {
                document.getElementById('timer').style.display = 'none';
            }
            
            showPage('quiz');
            displayQuestion();
        }

        // Timer
        function startTimer() {
            updateTimerDisplay();
            timer = setInterval(() => {
                timeLeft--;
                updateTimerDisplay();
                
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    endQuiz();
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            document.getElementById('time-display').textContent = 
                `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        // Mostra la domanda corrente
        function displayQuestion() {
            const question = currentQuiz[currentQuestionIndex];
            document.getElementById('current-question').textContent = currentQuestionIndex + 1;
            document.getElementById('total-questions').textContent = currentQuiz.length;
            document.getElementById('question-text').textContent = question.question;
            
            const answersContainer = document.getElementById('answers');
            answersContainer.innerHTML = '';
            
            question.options.forEach((option, index) => {
                const button = document.createElement('button');
                button.className = 'answer-btn';
                button.textContent = option;
                button.onclick = () => selectAnswer(option, button);
                answersContainer.appendChild(button);
            });
            
            document.getElementById('next-btn').style.display = 'none';
        }

        // Selezione risposta
        function selectAnswer(selectedAnswer, button) {
            const question = currentQuiz[currentQuestionIndex];
            const allButtons = document.querySelectorAll('.answer-btn');
            
            // Disabilita tutti i pulsanti
            allButtons.forEach(btn => {
                btn.style.pointerEvents = 'none';
                if (btn.textContent === question.correct) {
                    btn.classList.add('correct');
                } else if (btn === button) {
                    btn.classList.add('incorrect');
                }
            });
            
            // Verifica risposta
            if (selectedAnswer === question.correct) {
                score++;
            } else {
                wrongAnswers.push({
                    question: question.question,
                    correct: question.correct,
                    selected: selectedAnswer,
                    subject: question.subject
                });
            }
            
            document.getElementById('next-btn').style.display = 'block';
        }

        // Prossima domanda
        function nextQuestion() {
            currentQuestionIndex++;
            
            if (currentQuestionIndex < currentQuiz.length) {
                displayQuestion();
            } else {
                endQuiz();
            }
        }

        // Termina il quiz
        function endQuiz() {
            if (timer) {
                clearInterval(timer);
            }
            
            const percentage = Math.round((score / currentQuiz.length) * 100);
            
            document.getElementById('score-display').textContent = `${score}/${currentQuiz.length}`;
            document.getElementById('score-text').textContent = `${percentage}%`;
            
            const scoreDisplay = document.getElementById('score-display');
            const emojiDisplay = document.getElementById('score-emoji');
            
            if (percentage >= 80) {
                scoreDisplay.className = 'score good';
                emojiDisplay.textContent = '🎉 Eccellente! 🏆';
            } else if (percentage >= 60) {
                scoreDisplay.className = 'score average';
                emojiDisplay.textContent = '👍 Buon lavoro! 📚';
            } else {
                scoreDisplay.className = 'score poor';
                emojiDisplay.textContent = '💪 Continua a studiare! 📖';
            }
            
            // Mostra pulsante studio se ci sono errori
            if (wrongAnswers.length > 0) {
                document.getElementById('study-wrong-btn').style.display = 'inline-block';
                localStorage.setItem('wrongAnswers', JSON.stringify(wrongAnswers));
            }
            
            showPage('results');
        }

        // Modalità studio
        function showStudyMode() {
            const savedWrongAnswers = localStorage.getItem('wrongAnswers');
            const content = document.getElementById('study-content');
            
            if (savedWrongAnswers) {
                const wrongAnswers = JSON.parse(savedWrongAnswers);
                
                if (wrongAnswers.length === 0) {
                    content.innerHTML = '<p style="text-align: center;">🎉 Non hai errori da rivedere! Ottimo lavoro!</p>';
                } else {
                    content.innerHTML = '<h3>🔍 Rivedi le tue risposte sbagliate:</h3>';
                    
                    wrongAnswers.forEach((item, index) => {
                        const div = document.createElement('div');
                        div.className = 'study-mode';
                        div.innerHTML = `
                            <h4>Domanda ${index + 1}:</h4>
                            <p><strong>Materia:</strong> ${getSubjectName(item.subject)}</p>
                            <p><strong>Domanda:</strong> ${item.question}</p>
                            <p style="color: #dc3545;"><strong>La tua risposta:</strong> ${item.selected}</p>
                            <p style="color: #28a745;"><strong>Risposta corretta:</strong> ${item.correct}</p>
                            <p><strong>Spiegazione:</strong> ${getExplanation(item.subject, item.correct)}</p>
                        `;
                        content.appendChild(div);
                    });
                }
            } else {
                content.innerHTML = '<p style="text-align: center;">📚 Inizia un quiz per vedere qui le risposte da rivedere!</p>';
            }
            
            showPage('study');
        }

        // Ottieni nome materia
        function getSubjectName(subject) {
            const names = {
                'servizio': '🤝 Servizio Sociale',
                'etica': '⚖️ Etica e Deontologia',
                'penitenziario': '🏛️ Diritto Penitenziario',
                'penale': '👨‍⚖️ Diritto Penale e di Famiglia',
                'amministrativo': '📋 Diritto Amministrativo'
            };
            return names[subject] || subject;
        }

        // Ottieni spiegazione
        function getExplanation(subject, correct) {
            const explanations = {
                'servizio': 'Nel servizio sociale, questa risposta riflette i principi fondamentali della professione basati sulla valorizzazione della persona e sul processo di aiuto.',
                'etica': 'Questa risposta è conforme al Codice Deontologico degli Assistenti Sociali e ai principi etici della professione.',
                'penitenziario': 'Secondo la normativa penitenziaria vigente, questa è la disposizione corretta prevista dall\'ordinamento.',
                'penale': 'Questa risposta è conforme alle disposizioni del Codice Penale e del Codice di Procedura Penale.',
                'amministrativo': 'Secondo il diritto amministrativo e la Legge 241/1990, questa è la disciplina applicabile.'
            };
            return explanations[subject] || 'Questa è la risposta corretta secondo la normativa di riferimento.';
        }

        // Cancella dati studio
        function clearStudyData() {
            localStorage.removeItem('wrongAnswers');
            showStudyMode();
        }

        // Inizializzazione
        document.addEventListener('DOMContentLoaded', function() {
            // App pronta all'uso
            console.log('App Quiz Assistenti Sociali caricata con successo! 🚀');
        });
    </script>
</body>
</html>
