<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Placar dos Jogos - SENAC PAULISTA</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Estilos globais para o corpo da página */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F0F4F8; /* Light blue-grey, almost white */
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Align to top for better scrolling on smaller screens */
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
        }

        /* Contêiner principal da aplicação */
        .app-container {
            background-color: #ffffff;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 24px;
            max-width: 1200px;
            width: 100%;
            overflow-x: auto; /* Enable horizontal scrolling for small screens */
        }

        /* Estilos para as seções de página (esconde todas por padrão) */
        .page-section {
            display: none; /* All pages are hidden by default */
        }

        /* Estilo para a página ativa (mostra apenas a ativa) */
        .page-section.active {
            display: block; /* Only the active page is shown */
        }

        /* --- Estilos da Página Principal do Placar --- */
        #mainScoreboardPage .grid-header, #mainScoreboardPage .grid-row {
            display: grid;
            gap: 8px;
            padding: 12px 0;
            align-items: center;
            text-align: center;
        }

        #mainScoreboardPage .grid-header {
            background-color: #2196F3; /* Medium Blue */
            color: white;
            font-weight: 700;
            border-radius: 8px;
            margin-bottom: 12px;
            padding: 12px 8px;
            border: 1px solid #1976D2; /* Darker blue border */
        }

        #mainScoreboardPage .grid-header .header-orange-text {
            color: #FF9800; /* Orange text for specific header cells */
        }

        #mainScoreboardPage .grid-cell {
            padding: 8px;
            border-radius: 8px;
            background-color: #E3F2FD; /* Light Blue */
            display: flex;
            justify-content: center;
            align-items: center;
            min-width: 80px; /* Minimum width for cells */
        }

        #mainScoreboardPage .grid-row:nth-child(even) .grid-cell {
            background-color: #D1E6FA; /* Slightly darker light blue for even rows */
        }

        #mainScoreboardPage .grid-row input {
            width: 100%;
            padding: 6px;
            border: 1px solid #90CAF9; /* Lighter blue border */
            border-radius: 6px;
            text-align: center;
            background-color: #ffffff;
            font-weight: 600;
            color: #333;
            transition: border-color 0.2s ease;
        }

        #mainScoreboardPage .grid-row input:focus {
            outline: none;
            border-color: #FF9800; /* Orange focus */
            box-shadow: 0 0 0 2px rgba(255, 152, 0, 0.2);
        }

        #mainScoreboardPage .grid-row .team-name-display {
            text-align: left;
            padding-left: 12px;
            font-weight: 700;
            min-width: 120px; /* Ensure enough space for team names */
            color: #333333; /* Dark grey text */
            cursor: pointer; /* Indicate it's editable */
        }

        #mainScoreboardPage .grid-row .team-name-input {
            text-align: left;
            padding-left: 12px;
            font-weight: 700;
            min-width: 120px;
            color: #333333;
        }

        #mainScoreboardPage .grid-row .total-score {
            font-weight: 700;
            color: #333333;
            background-color: #FFECB3; /* Light Orange for total */
            box-shadow: inset 0 0 5px rgba(0,0,0,0.05); /* Subtle inner shadow */
        }

        #mainScoreboardPage .add-team-btn, #mainScoreboardPage .reset-btn, #mainScoreboardPage .edit-team-btn, #mainScoreboardPage .remove-team-btn, #mainScoreboardPage .modality-btn, #mainScoreboardPage .view-modality-scores-btn, #mainScoreboardPage .view-matches-btn, #mainScoreboardPage .print-report-btn {
            padding: 10px 16px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        #mainScoreboardPage .add-team-btn:hover, #mainScoreboardPage #addModalityBtn:hover {
            background-color: #F57C00; /* Dark Orange */
            transform: translateY(-2px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
        }

        #mainScoreboardPage .reset-btn {
            background-color: #1976D2; /* Dark Blue */
            color: white;
            margin-left: 10px;
        }

        #mainScoreboardPage .reset-btn:hover {
            background-color: #1565C0; /* Even darker blue */
            transform: translateY(-2px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
        }

        #mainScoreboardPage .edit-team-btn {
            background-color: #2196F3; /* Medium Blue */
            color: white;
            padding: 6px 10px;
            font-size: 0.875rem;
            line-height: 1;
            border-radius: 8px; /* Added border-radius for consistency */
            box-shadow: none;
        }

        #mainScoreboardPage .edit-team-btn:hover {
            background-color: #1976D2;
            transform: scale(1.05);
        }

        #mainScoreboardPage .remove-team-btn {
            background-color: #1976D2; /* Dark Blue for remove, consistent with reset */
            color: white;
            padding: 6px 10px;
            font-size: 0.875rem;
            line-height: 1;
            border-radius: 8px; /* Added border-radius for consistency */
            box-shadow: none;
        }

        #mainScoreboardPage .remove-team-btn:hover {
            background-color: #1565C0;
            transform: scale(1.05);
        }

        #mainScoreboardPage .button-group {
            display: flex;
            justify-content: center;
            margin-top: 20px;
            gap: 10px;
            flex-wrap: wrap; /* Allow buttons to wrap on smaller screens */
        }

        #mainScoreboardPage .user-id-display, #mainScoreboardPage .status-message {
            background-color: #E3F2FD; /* Light Blue */
            padding: 8px 12px;
            border-radius: 8px;
            margin-bottom: 16px;
            font-size: 0.9rem;
            color: #333333;
            text-align: center;
            word-break: break-all; /* Ensures long IDs wrap */
        }

        #mainScoreboardPage .status-message {
            background-color: #FFF3E0; /* Light orange for status */
            color: #E65100; /* Dark orange text */
            border: 1px solid #FFB74D; /* Medium orange border */
        }

        #mainScoreboardPage .error-message {
            background-color: #FFEBE9; /* Very light red for errors */
            color: #C62828; /* Dark red text */
            border: 1px solid #EF9A9A; /* Medium red border */
        }

        #mainScoreboardPage .empty-state-message {
            text-align: center;
            padding: 40px;
            color: #6b7280;
            font-size: 1.1rem;
            background-color: #f9fafb;
            border-radius: 8px;
            margin-top: 20px;
            border: 1px dashed #d1d5db;
        }

        #mainScoreboardPage .save-feedback {
            font-size: 0.75rem;
            color: #2e7d32;
            margin-left: 8px;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        #mainScoreboardPage .save-feedback.visible {
            opacity: 1;
        }

        /* Estilos dos Temporizadores */
        #mainScoreboardPage .timer-container {
            background-color: #E3F2FD; /* Light Blue */
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            padding: 20px;
            margin-bottom: 24px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }

        #mainScoreboardPage #timerDisplay {
            font-size: 3.5rem; /* Larger font for time */
            font-weight: 700;
            color: #1976D2; /* Dark Blue */
            letter-spacing: 2px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }
        /* Aumentado o tamanho da fonte para o cronômetro regressivo na página de confrontos */
        #matchScoreboardPage #matchPageCountdownDisplay,
        #detailedScoreboardPage #matchPageCountdownDisplay { /* Apply to detailed page as well */
            font-size: 8rem; /* Increased font size for countdown display */
            font-weight: 700;
            color: #1976D2; /* Dark Blue */
            letter-spacing: 2px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
            margin-top: 20px;
        }


        #mainScoreboardPage .timer-buttons button {
            padding: 12px 24px;
            border-radius: 10px;
            font-weight: 700;
            font-size: 1.1rem;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
            transition: all 0.3s ease;
        }

        #mainScoreboardPage .timer-buttons button:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
        }

        #mainScoreboardPage .timer-buttons button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            box-shadow: none;
        }

        #mainScoreboardPage .timer-buttons .bg-green-600 { background-color: #FF9800; } /* Orange */
        #mainScoreboardPage .timer-buttons .bg-green-600:hover:not(:disabled) { background-color: #F57C00; }
        #mainScoreboardPage .timer-buttons .bg-yellow-600 { background-color: #2196F3; color: white; } /* Blue */
        #mainScoreboardPage .timer-buttons .bg-yellow-600:hover:not(:disabled) { background-color: #1976D2; }
        #mainScoreboardPage .timer-buttons .bg-red-600 { background-color: #1976D2; } /* Dark Blue */
        #mainScoreboardPage .timer-buttons .bg-red-600:hover:not(:disabled) { background-color: #1565C0; }

        /* Estilos do Gerenciador de Modalidades */
        #mainScoreboardPage .modality-manager-container {
            background-color: #F0F4F8; /* Same as body background */
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 24px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        #mainScoreboardPage .modality-tag {
            background-color: #FF9800; /* Orange */
            color: white;
            padding: 6px 12px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 0.9rem;
            transition: background-color 0.2s ease;
        }

        #mainScoreboardPage .modality-tag:hover:not(.editing) {
            background-color: #F57C00; /* Darker Orange on hover */
        }

        #mainScoreboardPage .modality-tag .modality-name-display {
            flex-grow: 1;
            cursor: pointer; /* Indicate it's editable */
        }

        #mainScoreboardPage .modality-tag .modality-name-input {
            background-color: white;
            border: 1px solid #90CAF9; /* Lighter blue border */
            border-radius: 4px;
            padding: 2px 6px;
            color: #333;
            font-weight: 600;
            width: auto; /* Adjust width dynamically */
            min-width: 50px;
            max-width: 150px; /* Limit max width */
            box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);
        }

        #mainScoreboardPage .modality-tag .modality-action-btn {
            background-color: #2196F3; /* Blue for modality actions */
            color: white;
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 0.75rem;
            cursor: pointer;
            transition: background-color 0.2s ease, transform 0.1s ease;
            box-shadow: none;
            margin-left: 4px;
        }

        #mainScoreboardPage .modality-tag .modality-action-btn:hover {
            background-color: #1976D2;
            transform: translateY(-1px);
        }

        #mainScoreboardPage .countdown-setup {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }

        #mainScoreboardPage .countdown-setup input {
            width: 60px;
            text-align: center;
            padding: 8px;
            border: 1px solid #90CAF9;
            border-radius: 6px;
            font-weight: 600;
        }

        #mainScoreboardPage .view-modality-scores-btn, #mainScoreboardPage .view-matches-btn {
            background-color: #007bff; /* Blue */
            color: white;
        }

        #mainScoreboardPage .view-modality-scores-btn:hover, #mainScoreboardPage .view-matches-btn:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
        }

        #mainScoreboardPage .print-report-btn {
            background-color: #28a745; /* Green for print button */
            color: white;
        }

        #mainScoreboardPage .print-report-btn:hover {
            background-color: #218838;
            transform: translateY(-2px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
        }


        /* --- Estilos da Página de Seleção de Modalidades --- */
        #modalitiesPage .container {
            background-color: #ffffff;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 24px;
            max-width: 600px;
            width: 100%;
            text-align: center;
        }

        #modalitiesPage .modality-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }

        #modalitiesPage .modality-button {
            background-color: #2196F3; /* Medium Blue */
            color: white;
            padding: 15px 25px;
            border-radius: 10px;
            font-size: 1.2rem;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-decoration: none;
            display: block;
        }

        #modalitiesPage .modality-button:hover {
            background-color: #1976D2; /* Darker Blue */
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        #modalitiesPage .back-button {
            background-color: #6c757d; /* Grey */
            color: white;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            margin-top: 30px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        #modalitiesPage .back-button:hover {
            background-color: #5a6268;
            transform: translateY(-1px);
        }

        #modalitiesPage .empty-state-message {
            text-align: center;
            padding: 20px;
            color: #6b7280;
            font-size: 1.1rem;
            background-color: #f9fafb;
            border-radius: 8px;
            margin-top: 20px;
            border: 1px dashed #d1d5db;
        }

        /* --- Estilos da Página de Placar Detalhado --- */
        #detailedScoreboardPage .scoreboard-detail-container {
            background-color: #ffffff;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 24px;
            max-width: 800px;
            width: 100%;
            text-align: center;
        }

        #detailedScoreboardPage .header-section {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap; /* Allow wrapping on small screens */
            gap: 10px;
        }

        #detailedScoreboardPage .header-section h1 {
            font-size: 2.5rem; /* Larger font for modality name */
            font-weight: 700;
            color: #1976D2; /* Dark Blue */
            flex-grow: 1; /* Allow title to take available space */
            text-align: center;
        }

        #detailedScoreboardPage .score-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #E3F2FD; /* Light Blue */
            padding: 20px 30px;
            margin-bottom: 15px;
            border-radius: 12px;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.05);
        }

        #detailedScoreboardPage .score-item:nth-child(even) {
            background-color: #D1E6FA; /* Slightly darker light blue for even rows */
        }

        #detailedScoreboardPage .team-name {
            font-size: 2rem; /* Larger font for team name */
            font-weight: 600;
            color: #333333;
            flex-grow: 1;
            text-align: left;
        }

        #detailedScoreboardPage .team-score {
            font-size: 3rem; /* Very large font for score */
            font-weight: 800;
            color: #FF9800; /* Orange */
            min-width: 80px; /* Ensure space for score */
            text-align: right;
        }

        #detailedScoreboardPage .no-data-message {
            text-align: center;
            padding: 40px;
            color: #6b7280;
            font-size: 1.1rem;
            background-color: #f9fafb;
            border-radius: 8px;
            margin-top: 20px;
            border: 1px dashed #d1d5db;
        }

        #detailedScoreboardPage .button-group {
            display: flex;
            justify-content: center;
            margin-top: 30px;
            gap: 15px;
            flex-wrap: wrap;
        }

        #detailedScoreboardPage .back-button, #detailedScoreboardPage .home-button {
            padding: 12px 24px;
            border-radius: 10px;
            font-weight: 700;
            font-size: 1.1rem;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        #detailedScoreboardPage .back-button {
            background-color: #6c757d; /* Grey */
            color: white;
        }

        #detailedScoreboardPage .back-button:hover {
            background-color: #5a6268;
            transform: translateY(-2px);
        }

        #detailedScoreboardPage .home-button {
            background-color: #007bff; /* Blue */
            color: white;
        }

        #detailedScoreboardPage .home-button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }

        /* --- Estilos da Página de Confrontos de Equipes --- */
        #matchScoreboardPage .container {
            background-color: #ffffff;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 24px;
            max-width: 800px;
            width: 100%;
            text-align: center;
        }

        #matchScoreboardPage .create-match-section {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
            align-items: center;
            margin-bottom: 30px;
            padding: 20px;
            background-color: #E3F2FD;
            border-radius: 12px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }

        #matchScoreboardPage .create-match-section select {
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #90CAF9;
            background-color: white;
            font-size: 1rem;
            font-weight: 600;
            color: #333;
            min-width: 150px;
        }

        #matchScoreboardPage .start-new-match-btn {
            background-color: #FF9800;
            color: white;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        #matchScoreboardPage .start-new-match-btn:hover {
            background-color: #F57C00;
            transform: translateY(-2px);
        }

        #matchScoreboardPage .match-list,
        #detailedScoreboardPage .match-list { /* Apply match list styling to detailed page as well */
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        #matchScoreboardPage .match-item,
        #detailedScoreboardPage .match-item { /* Apply match item styling to detailed page as well */
            background-color: #D1E6FA; /* Light Blue for match item */
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            gap: 15px;
            align-items: center;
            position: relative;
        }

        #matchScoreboardPage .match-teams-display,
        #detailedScoreboardPage .match-teams-display { /* Apply to detailed page as well */
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            gap: 20px;
        }

        #matchScoreboardPage .match-team-block,
        #detailedScoreboardPage .match-team-block { /* Apply to detailed page as well */
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }

        /* Aumentado o tamanho da fonte para os nomes das equipes nos confrontos */
        #matchScoreboardPage .match-team-name,
        #detailedScoreboardPage .match-team-name { /* Apply to detailed page as well */
            font-size: 4rem; /* Increased font size for team names in matches */
            font-weight: 700;
            color: #333;
            text-align: center;
            word-break: break-word;
        }
        
        /* Aumentado o tamanho da fonte para os placares nos confrontos */
        #matchScoreboardPage .match-score-input,
        #detailedScoreboardPage .match-score-input { /* Apply to detailed page as well */
            width: 100px; /* Adjusted width for larger font */
            padding: 10px;
            font-size: 5rem; /* Increased font size for score input */
            font-weight: 800;
            text-align: center;
            border: 2px solid #FF9800;
            border-radius: 8px;
            background-color: white;
            color: #FF9800;
        }

        #matchScoreboardPage .match-score-input:focus {
            outline: none;
            border-color: #F57C00;
            box-shadow: 0 0 0 3px rgba(255, 152, 0, 0.3);
        }

        #matchScoreboardPage .match-vs-text,
        #detailedScoreboardPage .match-vs-text { /* Apply to detailed page as well */
            font-size: 3rem; /* Increased font size */
            font-weight: 700;
            color: #2196F3;
        }
        #matchScoreboardPage .end-match-btn {
            background-color: #DC3545; /* Red */
            color: white;
            padding: 8px 15px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            position: absolute;
            top: 15px;
            right: 15px;
        }
        #matchScoreboardPage .end-match-btn:hover {
            background-color: #C82333;
            transform: translateY(-1px);
        }

        /* --- Estilos do Modal (Global) --- */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6); /* Darker overlay */
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease, visibility 0.3s ease;
        }

        .modal.visible {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background-color: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3); /* Stronger shadow */
            text-align: center;
            max-width: 400px;
            width: 90%;
            transform: translateY(-20px);
            transition: transform 0.3s ease;
        }

        .modal.visible .modal-content {
            transform: translateY(0);
        }

        .modal-buttons {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .modal-buttons button {
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .modal-buttons .confirm-btn {
            background-color: #FF9800; /* Orange confirm */
            color: white;
        }

        .modal-buttons .confirm-btn:hover {
            background-color: #F57C00;
            transform: translateY(-1px);
        }

        .modal-buttons .cancel-btn {
            background-color: #E0E0E0; /* Light grey cancel */
            color: #333;
        }

        .modal-buttons .cancel-btn:hover {
            background-color: #BDBDBD;
            transform: translateY(-1px);
        }

        /* Estilos específicos para impressão */
        @media print {
            body > *:not(.print-container) {
                display: none !important;
            }
            .print-container {
                display: block !important;
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background-color: white;
                padding: 20px;
                box-sizing: border-box;
                font-family: 'Inter', sans-serif;
                color: black;
            }
            .print-container h1, .print-container h2 {
                color: black !important;
            }
            .print-container .grid-header, .print-container .grid-row, .print-container .score-item, .print-container .match-item {
                border: 1px solid #ccc;
                margin-bottom: 5px;
                padding: 10px;
                break-inside: avoid; /* Evita quebrar esses elementos entre as páginas */
            }
            .print-container .grid-cell, .print-container .match-team-block {
                background-color: #f0f0f0 !important; /* Light grey for print cells */
                color: black !important;
            }
            .print-container .total-score, .print-container .team-score, .print-container .match-score-input {
                background-color: #fdd8b8 !important; /* Light orange for scores in print */
                color: black !important;
            }
            /* Esconde botões/controles específicos de impressão */
            .print-container .print-hide {
                display: none !important;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Seção da Página Principal do Placar -->
        <div id="mainScoreboardPage" class="page-section active">
            <h1 class="text-4xl font-extrabold text-center text-blue-800 mb-6">SENAC PAULISTA</h1>
            <h1 class="text-3xl font-bold text-center text-gray-800 mb-6">Placar dos Jogos</h1>
            <div class="user-id-display" id="userIdDisplay">Dados salvos localmente no navegador</div>
            <div class="status-message hidden" id="statusMessage"></div>

            <!-- Temporizador Crescente (Tempo de Jogo) -->
            <div class="timer-container">
                <h2 class="text-2xl font-semibold text-gray-700">Tempo de Jogo (Contador Crescente)</h2>
                <div id="timerDisplay">00:00:00</div>
                <div class="timer-buttons">
                    <button id="startTimerBtn" class="bg-green-600 text-white">Iniciar</button>
                    <button id="pauseTimerBtn" class="bg-yellow-600 text-white">Pausar</button>
                    <button id="resetTimerBtn" class="bg-red-600 text-white">Reiniciar</button>
                </div>
            </div>

            <!-- Gerenciador de Modalidades -->
            <div class="modality-manager-container">
                <h2 class="text-xl font-semibold text-gray-700 mb-4">Gerenciar Modalidades</h2>
                <div class="flex flex-wrap items-center gap-4 mb-4">
                    <input type="text" id="newModalityName" placeholder="Nome da Nova Modalidade" class="flex-grow p-2 border rounded-md" maxlength="20">
                    <button id="addModalityBtn" class="add-team-btn modality-btn">Adicionar Modalidade</button>
                </div>
                <div id="currentModalities" class="flex flex-wrap gap-2"></div>
            </div>

            <!-- Cabeçalho da Tabela do Placar -->
            <div class="grid-header" id="gridHeader"></div>
            <!-- Corpo da Tabela do Placar (preenchido por JS) -->
            <div id="scoreboard-body">
                <div id="loadingIndicator" class="empty-state-message hidden">Carregando placar...</div>
                <div id="emptyState" class="empty-state-message hidden">
                    Nenhuma turma adicionada ainda. Clique em "Adicionar Turma" para começar!
                </div>
            </div>

            <!-- Botões de Ação do Placar Principal -->
            <div class="button-group">
                <button id="addTeamBtn" class="add-team-btn">Adicionar Turma</button>
                <button id="resetScoresBtn" class="reset-btn">Reiniciar Placar</button>
                <button id="viewModalityScoresBtn" class="view-modality-scores-btn">Placar por Modalidade</button>
                <button id="viewMatchesBtn" class="view-matches-btn">Gerenciar Confrontos</button>
                <button id="printReportBtn" class="print-report-btn">Imprimir Relatório</button>
            </div>
        </div>

        <!-- Seção da Página de Seleção de Modalidades -->
        <div id="modalitiesPage" class="page-section">
            <div class="container">
                <h1 class="text-3xl font-bold text-gray-800 mb-6">Escolha a Modalidade</h1>
                <!-- Lista de botões de modalidade (preenchido por JS) -->
                <div id="modalityList" class="modality-list">
                    <div id="noModalitiesMessage" class="empty-state-message hidden">
                        Nenhuma modalidade adicionada ainda. Adicione modalidades na página principal.
                    </div>
                </div>
                <!-- Botão de Voltar para a página principal -->
                <button id="modalitiesPageBackButton" class="back-button">Voltar</button>
            </div>
        </div>

        <!-- Seção da Página de Placar Detalhado por Modalidade -->
        <div id="detailedScoreboardPage" class="page-section">
            <div class="scoreboard-detail-container">
                <!-- Nome da Modalidade (preenchido por JS) -->
                <div class="header-section">
                    <h1 id="modalityNameDisplay"></h1>
                </div>
                <!-- Pontuações detalhadas por equipe (preenchido por JS) -->
                <div id="detailedScores" class="score-list">
                    <div id="noScoresMessage" class="no-data-message hidden">
                        Nenhum placar disponível para esta modalidade.
                    </div>
                </div>

                <!-- Nova Seção: Confrontos Ativos Nesta Modalidade -->
                <h2 class="text-xl font-semibold text-gray-700 mt-8 mb-4">Confrontos Ativos Nesta Modalidade</h2>
                <div class="match-list" id="modalitySpecificMatchesContainer">
                    <div class="empty-state-message hidden" id="noModalityMatchesMessage">
                        Nenhum confronto ativo para esta modalidade.
                    </div>
                </div>

                <!-- Botões de navegação para a página detalhada -->
                <div class="button-group">
                    <button id="detailedPageBackButton" class="back-button">Voltar</button>
                    <button id="detailedPageHomeButton" class="home-button">Voltar ao Início</button>
                </div>
            </div>
        </div>

        <!-- Nova Seção: Página de Confrontos de Equipes -->
        <div id="matchScoreboardPage" class="page-section">
            <div class="container">
                <h1 class="text-3xl font-bold text-gray-800 mb-6">Gerenciar Confrontos de Equipes</h1>

                <!-- Contador Regressivo (display e controles) -->
                <div class="timer-container">
                    <h2 class="text-2xl font-semibold text-gray-700">Contador Regressivo do Confronto</h2>
                    <div class="countdown-setup">
                        <label for="countdownMinutes">Minutos:</label>
                        <input type="number" id="countdownMinutes" value="0" min="0" max="59" class="p-2 border rounded-md">
                        <label for="countdownSeconds">Segundos:</label>
                        <input type="number" id="countdownSeconds" value="0" min="0" max="59" class="p-2 border rounded-md">
                    </div>
                    <div id="matchPageCountdownDisplay">00:00</div>
                    <div class="timer-buttons">
                        <button id="startCountdownBtn" class="bg-green-600 text-white">Iniciar Regressiva</button>
                        <button id="pauseCountdownBtn" class="bg-yellow-600 text-white">Pausar Regressiva</button>
                        <button id="resetCountdownBtn" class="bg-red-600 text-white">Reiniciar Regressiva</button>
                    </div>
                </div>

                <div class="create-match-section mt-8">
                    <h2 class="text-xl font-semibold text-gray-700 mb-4 w-full">Iniciar Novo Confronto</h2>
                    <select id="matchModalitySelect" class="p-2 border rounded-md"></select>
                    <select id="team1Select" class="p-2 border rounded-md"></select>
                    <span class="match-vs-text">vs.</span>
                    <select id="team2Select" class="p-2 border rounded-md"></select>
                    <button id="startNewMatchBtn" class="start-new-match-btn">Iniciar Confronto</button>
                </div>

                <h2 class="text-xl font-semibold text-gray-700 mt-8 mb-4">Confrontos Ativos</h2>
                <div class="match-list" id="activeMatchesContainer">
                    <div class="empty-state-message hidden" id="noActiveMatchesMessage">
                        Nenhum confronto ativo. Selecione equipes para iniciar.
                    </div>
                </div>

                <div class="button-group">
                    <button id="matchScoreboardPageBackButton" class="back-button">Voltar</button>
                    <button id="matchScoreboardPageHomeButton" class="home-button">Voltar ao Início</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Confirmação (Global) -->
    <div id="confirmationModal" class="modal hidden">
        <div class="modal-content">
            <p id="modalMessage" class="text-lg font-semibold text-gray-700 mb-4"></p>
            <div class="modal-buttons">
                <button id="modalConfirmBtn" class="confirm-btn">Confirmar</button>
                <button id="modalCancelBtn" class="cancel-btn">Cancelar</button>
            </div>
        </div>
    </div>

    <!-- Container for Print Report (hidden by default) -->
    <div id="printContainer" class="print-container" style="display: none;"></div>

    <script type="module">
        // Variáveis globais para dados e estado da aplicação
        let allTeams = [];
        let allModalities = [];
        let activeMatches = []; // Variável para armazenar confrontos ativos
        let currentActivePage = 'mainScoreboardPage'; // Rastreia a página atualmente ativa

        // --- Elementos do DOM (obtidos uma vez para otimização) ---
        // Elementos da Página Principal do Placar
        const mainScoreboardPage = document.getElementById('mainScoreboardPage');
        const statusMessageElement = document.getElementById('statusMessage');
        const loadingIndicator = document.getElementById('loadingIndicator');
        const emptyStateMessage = document.getElementById('emptyState');
        const scoreboardBody = document.getElementById('scoreboard-body');
        const gridHeader = document.getElementById('gridHeader');
        const userIdDisplay = document.getElementById('userIdDisplay');

        // Elementos do Temporizador Crescente
        let timerInterval = null;
        let startTime = 0;
        let elapsedTime = 0;
        let isRunning = false;
        const timerDisplay = document.getElementById('timerDisplay');
        const startTimerBtn = document.getElementById('startTimerBtn');
        const pauseTimerBtn = document.getElementById('pauseTimerBtn');
        const resetTimerBtn = document.getElementById('resetTimerBtn');

        // Elementos do Gerenciador de Modalidades
        const newModalityNameInput = document.getElementById('newModalityName');
        const addModalityBtn = document.getElementById('addModalityBtn');
        const currentModalitiesContainer = document.getElementById('currentModalities');
        const addTeamBtn = document.getElementById('addTeamBtn');
        const resetScoresBtn = document.getElementById('resetScoresBtn');
        const viewModalityScoresBtn = document.getElementById('viewModalityScoresBtn');
        const viewMatchesBtn = document.getElementById('viewMatchesBtn'); // Botão para confrontos
        const printReportBtn = document.getElementById('printReportBtn'); // Botão para relatório de impressão

        // Elementos da Página de Seleção de Modalidades
        const modalitiesPage = document.getElementById('modalitiesPage');
        const modalityListContainer = document.getElementById('modalityList');
        const noModalitiesMessage = document.getElementById('noModalitiesMessage');
        const modalitiesPageBackButton = document.getElementById('modalitiesPageBackButton');

        // Elementos da Página de Placar Detalhado
        const detailedScoreboardPage = document.getElementById('detailedScoreboardPage');
        const modalityNameDisplay = document.getElementById('modalityNameDisplay');
        const detailedScoresContainer = document.getElementById('detailedScores');
        const noScoresMessage = document.getElementById('noScoresMessage');
        const detailedPageBackButton = document.getElementById('detailedPageBackButton');
        const detailedPageHomeButton = document.getElementById('detailedPageHomeButton');
        const modalitySpecificMatchesContainer = document.getElementById('modalitySpecificMatchesContainer');
        const noModalityMatchesMessage = document.getElementById('noModalityMatchesMessage');

        // Elementos da Página de Confrontos de Equipes
        const matchScoreboardPage = document.getElementById('matchScoreboardPage');
        const team1Select = document.getElementById('team1Select');
        const team2Select = document.getElementById('team2Select');
        const startNewMatchBtn = document.getElementById('startNewMatchBtn');
        const activeMatchesContainer = document.getElementById('activeMatchesContainer');
        const noActiveMatchesMessage = document.getElementById('noActiveMatchesMessage');
        const matchScoreboardPageBackButton = document.getElementById('matchScoreboardPageBackButton');
        const matchScoreboardPageHomeButton = document.getElementById('matchScoreboardPageHomeButton');
        
        // Elementos do Temporizador Regressivo (movidos para a Página de Confrontos)
        let countdownInterval = null;
        let countdownRemainingTime = 0; // em milissegundos
        let isCountdownRunning = false;
        const countdownMinutesInput = document.getElementById('countdownMinutes');
        const countdownSecondsInput = document.getElementById('countdownSeconds');
        const startCountdownBtn = document.getElementById('startCountdownBtn');
        const pauseCountdownBtn = document.getElementById('pauseCountdownBtn');
        const resetCountdownBtn = document.getElementById('resetCountdownBtn');
        const matchPageCountdownDisplay = document.getElementById('matchPageCountdownDisplay'); // Display do cronômetro regressivo na página de confrontos

        const printContainer = document.getElementById('printContainer'); // Elemento do contêiner de impressão
        const matchModalitySelect = document.getElementById('matchModalitySelect'); // Elemento de seleção de modalidade para confrontos

        // --- Funções Essenciais da Aplicação ---

        /**
         * Alterna a visibilidade das seções da "página".
         * @param {string} pageId - O ID da seção a ser exibida.
         */
        function showPage(pageId) {
            document.querySelectorAll('.page-section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
            currentActivePage = pageId; // Atualiza a página ativa atual

            // Ações específicas ao mudar de página
            if (pageId === 'matchScoreboardPage') {
                populateTeamSelectors(); // Popula os seletores de equipe
                populateMatchModalitySelector(); // Popula o seletor de modalidade para confrontos
                renderMatchScoreboardPage(); // Renderiza os confrontos ativos
                updateCountdownDisplay(); // Atualiza o display do cronômetro regressivo imediatamente
            }
        }

        /**
         * Gera um ID único simples para elementos locais.
         * @returns {string} Um ID único.
         */
        function generateUniqueId() {
            return '_' + Math.random().toString(36).substr(2, 9);
        }

        /**
         * Exibe uma mensagem de status temporária na interface.
         * @param {string} message - A mensagem a ser exibida.
         * @param {string} type - O tipo de mensagem ('status' ou 'error').
         */
        function showStatusMessage(message, type = 'status') {
            statusMessageElement.textContent = message;
            statusMessageElement.classList.remove('hidden', 'status-message', 'error-message');
            statusMessageElement.classList.add(type === 'error' ? 'error-message' : 'status-message');
            setTimeout(() => {
                statusMessageElement.classList.add('hidden');
            }, 5000); // Esconde após 5 segundos
        }

        /**
         * Exibe um modal de confirmação personalizado.
         * @param {string} message - A mensagem a ser exibida no modal.
         * @param {Function} onConfirm - A função a ser executada se o usuário confirmar.
         * @returns {Promise<boolean>} Uma promessa que resolve para true se confirmado, false se cancelado.
         */
        function showConfirmationModal(message, onConfirm) {
            const modal = document.getElementById('confirmationModal');
            const modalMessage = document.getElementById('modalMessage');
            const modalConfirmBtn = document.getElementById('modalConfirmBtn');
            const modalCancelBtn = document.getElementById('modalCancelBtn');

            modalMessage.textContent = message;
            modal.classList.add('visible');

            return new Promise((resolve) => {
                const handleConfirm = () => {
                    modal.classList.remove('visible');
                    modalConfirmBtn.removeEventListener('click', handleConfirm);
                    modalCancelBtn.removeEventListener('click', handleCancel);
                    onConfirm(); // Executa a ação se confirmado
                    resolve(true);
                };

                const handleCancel = () => {
                    modal.classList.remove('visible');
                    modalConfirmBtn.removeEventListener('click', handleConfirm);
                    modalCancelBtn.removeEventListener('click', handleCancel);
                    resolve(false);
                };

                modalConfirmBtn.addEventListener('click', handleConfirm);
                modalCancelBtn.addEventListener('click', handleCancel);
            });
        }

        // --- Funções de Persistência de Dados (localStorage) ---
        function saveData() {
            try {
                localStorage.setItem('allTeams', JSON.stringify(allTeams));
                localStorage.setItem('allModalities', JSON.stringify(allModalities));
                localStorage.setItem('activeMatches', JSON.stringify(activeMatches)); // Salva os confrontos ativos
                localStorage.setItem('timerElapsedTime', elapsedTime.toString());
                localStorage.setItem('timerIsRunning', isRunning.toString());
                localStorage.setItem('timerStartTime', startTime.toString());
                localStorage.setItem('countdownRemainingTime', countdownRemainingTime.toString());
                localStorage.setItem('isCountdownRunning', isCountdownRunning.toString());
                userIdDisplay.textContent = 'Dados salvos localmente no navegador';
            } catch (e) {
                console.error("Erro ao salvar dados no localStorage:", e);
                showStatusMessage("Erro ao salvar dados localmente. Verifique o espaço de armazenamento do navegador.", 'error');
            }
        }

        function loadData() {
            try {
                const storedTeams = localStorage.getItem('allTeams');
                const storedModalities = localStorage.getItem('allModalities');
                const storedActiveMatches = localStorage.getItem('activeMatches'); // Carrega confrontos ativos
                const storedElapsedTime = localStorage.getItem('timerElapsedTime');
                const storedIsRunning = localStorage.getItem('timerIsRunning');
                const storedStartTime = localStorage.getItem('timerStartTime');
                const storedCountdownRemainingTime = localStorage.getItem('countdownRemainingTime');
                const storedIsCountdownRunning = localStorage.getItem('isCountdownRunning');

                // Define modalidades padrão
                const defaultModalities = [
                    { id: 'cultura', name: 'Apresentação Cultural', order: 1 },
                    { id: 'xadrez', name: 'Xadrez', order: 2 },
                    { id: 'domino', name: 'Dominó', order: 3 },
                    { id: 'jogosDigitais', name: 'Jogos Digitais (FIFA)', order: 4 },
                    { id: 'queimado', name: 'Queimado', order: 5 },
                    { id: 'futsalMasc', name: 'Futsal (masculino)', order: 6 },
                    { id: 'futsalFem', name: 'Futsal (feminino)', order: 7 },
                    { id: 'tenisMesa', name: 'Tenis de Mesa', order: 8 },
                    { id: 'volei', name: 'Vôlei', order: 9 },
                    { id: 'handebolFem', name: 'Handebol (feminino)', order: 10 },
                    { id: 'handebolMasc', name: 'Handebol (masculino)', order: 11 }
                ];

                if (storedModalities) {
                    allModalities = JSON.parse(storedModalities);
                    // Filtra modalidades indesejadas que podem ter sido salvas anteriormente
                    allModalities = allModalities.filter(modality =>
                        modality.name !== 'Jogo de Bola' && modality.name !== 'Corrida'
                    );
                } else {
                    allModalities = []; // Inicia vazio se não houver modalidades armazenadas
                }

                // Mescla novas modalidades padrão, mantendo as existentes e sua ordem
                const existingModalityIds = new Set(allModalities.map(m => m.id));
                defaultModalities.forEach(defaultMod => {
                    if (!existingModalityIds.has(defaultMod.id)) {
                        allModalities.push(defaultMod);
                    }
                });
                allModalities.sort((a, b) => a.order - b.order); // Reordena para manter a ordem

                // Define equipes padrão
                const defaultTeams = [
                    { id: 'team1A', name: '1A' },
                    { id: 'team1B', name: '1B' },
                    { id: 'team1C', name: '1C' },
                    { id: 'team2A', name: '2A' },
                    { id: 'team2B', name: '2B' },
                    { id: 'team3A', name: '3A' }
                ];

                if (storedTeams) {
                    allTeams = JSON.parse(storedTeams);
                } else {
                    allTeams = []; // Inicia vazio se não houver equipes armazenadas
                }

                // Mescla novas equipes padrão, mantendo as existentes
                const existingTeamIds = new Set(allTeams.map(t => t.id));
                defaultTeams.forEach(defaultTeam => {
                    if (!existingTeamIds.has(defaultTeam.id)) {
                        allTeams.push(defaultTeam);
                    }
                });

                // Garante que todas as equipes tenham pontuações para todas as modalidades atuais
                allTeams.forEach(team => {
                    if (!team.scores) {
                        team.scores = {};
                    }
                    allModalities.forEach(modality => {
                        if (team.scores[modality.id] === undefined) {
                            team.scores[modality.id] = 0;
                        }
                    });
                    // Remove pontuações para modalidades que não existem mais
                    for (const modId in team.scores) {
                        if (!allModalities.some(m => m.id === modId)) {
                            delete team.scores[modId];
                        }
                    }
                    team.total = calculateTotal(team); // Recalcula o total após as atualizações
                });

                if (storedActiveMatches) {
                    activeMatches = JSON.parse(storedActiveMatches);
                } else {
                    activeMatches = [];
                }

                // Carrega o estado do Temporizador Crescente
                if (storedElapsedTime) {
                    elapsedTime = parseInt(storedElapsedTime, 10);
                }
                if (storedIsRunning === 'true') {
                    isRunning = true;
                } else {
                    isRunning = false;
                }
                if (storedStartTime) {
                    startTime = parseInt(storedStartTime, 10);
                }

                if (isRunning) {
                    startTime = Date.now() - elapsedTime; // Recalcula startTime para manter a precisão
                    timerInterval = setInterval(updateTimerDisplay, 1000);
                    startTimerBtn.disabled = true;
                    pauseTimerBtn.disabled = false;
                } else {
                    updateTimerDisplay(); // Atualiza a exibição mesmo se não estiver rodando
                }

                // Carrega o estado do Temporizador Regressivo
                if (storedCountdownRemainingTime) {
                    countdownRemainingTime = parseInt(storedCountdownRemainingTime, 10);
                } else {
                    countdownRemainingTime = 0;
                }
                if (storedIsCountdownRunning === 'true') {
                    isCountdownRunning = true;
                } else {
                    isCountdownRunning = false;
                }

                if (isCountdownRunning) {
                    countdownInterval = setInterval(updateCountdownDisplay, 1000);
                    startCountdownBtn.disabled = true;
                    pauseCountdownBtn.disabled = false;
                    countdownMinutesInput.disabled = true;
                    countdownSecondsInput.disabled = true;
                } else {
                    updateCountdownDisplay(); // Atualiza a exibição mesmo se não estiver rodando
                }

                userIdDisplay.textContent = 'Dados carregados do navegador';
            } catch (e) {
                console.error("Erro ao carregar dados do localStorage:", e);
                showStatusMessage("Erro ao carregar dados localmente. Os dados podem estar corrompidos.", 'error');
                // Limpa dados corrompidos para evitar problemas futuros
                localStorage.clear();
                allTeams = [];
                allModalities = [];
                activeMatches = [];
                elapsedTime = 0;
                isRunning = false;
                startTime = 0;
                countdownRemainingTime = 0;
                isCountdownRunning = false;
            }
        }
        // --- Fim das Funções de Persistência ---

        // --- Funções do Temporizador Crescente ---
        function formatTime(ms) {
            const totalSeconds = Math.floor(ms / 1000);
            const hours = Math.floor((totalSeconds % 86400) / 3600);
            const minutes = Math.floor((totalSeconds % 3600) / 60);
            const seconds = totalSeconds % 60;
            const pad = (num) => num.toString().padStart(2, '0');
            return `${pad(hours)}:${pad(minutes)}:${pad(seconds)}`;
        }

        function updateTimerDisplay() {
            const currentTime = Date.now();
            const currentElapsedTime = elapsedTime + (isRunning ? (currentTime - startTime) : 0);
            timerDisplay.textContent = formatTime(currentElapsedTime);
            saveData();
        }

        function startTimer() {
            if (!isRunning) {
                startTime = Date.now() - elapsedTime;
                timerInterval = setInterval(updateTimerDisplay, 1000);
                isRunning = true;
                startTimerBtn.disabled = true;
                pauseTimerBtn.disabled = false;
                saveData();
            }
        }

        function pauseTimer() {
            if (isRunning) {
                clearInterval(timerInterval);
                elapsedTime = Date.now() - startTime;
                isRunning = false;
                startTimerBtn.disabled = false;
                pauseTimerBtn.disabled = true;
                saveData();
            }
        }

        function resetTimer() {
            clearInterval(timerInterval);
            elapsedTime = 0;
            isRunning = false;
            timerDisplay.textContent = formatTime(0);
            startTimerBtn.disabled = false;
            pauseTimerBtn.disabled = true;
            saveData();
        }

        // Adiciona event listeners para os botões do temporizador crescente
        startTimerBtn.addEventListener('click', startTimer);
        pauseTimerBtn.addEventListener('click', pauseTimer);
        resetTimerBtn.addEventListener('click', resetTimer);

        // --- Funções do Temporizador Regressivo ---
        function formatCountdownTime(ms) {
            const totalSeconds = Math.floor(ms / 1000);
            const minutes = Math.floor(totalSeconds / 60);
            const seconds = totalSeconds % 60;
            const pad = (num) => num.toString().padStart(2, '0');
            return `${pad(minutes)}:${pad(seconds)}`;
        }

        function updateCountdownDisplay() {
            const formattedTime = formatCountdownTime(countdownRemainingTime);
            // Atualiza o display do cronômetro regressivo, onde quer que ele esteja
            if (matchPageCountdownDisplay) {
                matchPageCountdownDisplay.textContent = formattedTime;
            }

            if (countdownRemainingTime <= 0) {
                clearInterval(countdownInterval);
                isCountdownRunning = false;
                countdownRemainingTime = 0; // Garante que fique em 00:00
                showStatusMessage("Tempo esgotado!");
            } else if (isCountdownRunning) {
                countdownRemainingTime -= 1000;
            }
            saveData();
        }

        function startCountdown() {
            if (!isCountdownRunning) {
                const minutes = parseInt(countdownMinutesInput.value, 10) || 0;
                const seconds = parseInt(countdownSecondsInput.value, 10) || 0;

                // Se o tempo restante for 0, usa os valores dos inputs para definir o tempo inicial
                if (countdownRemainingTime === 0) {
                    countdownRemainingTime = (minutes * 60 + seconds) * 1000;
                }

                if (countdownRemainingTime <= 0) {
                    showStatusMessage("Por favor, defina um tempo para o contador regressivo.", 'error');
                    return;
                }

                isCountdownRunning = true;
                countdownInterval = setInterval(updateCountdownDisplay, 1000);
                startCountdownBtn.disabled = true;
                pauseCountdownBtn.disabled = false;
                countdownMinutesInput.disabled = true;
                countdownSecondsInput.disabled = true;
                saveData();
            }
        }

        function pauseCountdown() {
            if (isCountdownRunning) {
                clearInterval(countdownInterval);
                isCountdownRunning = false;
                startCountdownBtn.disabled = false;
                pauseCountdownBtn.disabled = true;
                countdownMinutesInput.disabled = false;
                countdownSecondsInput.disabled = false;
                saveData();
            }
        }

        function resetCountdown() {
            clearInterval(countdownInterval);
            isCountdownRunning = false;
            countdownRemainingTime = 0;
            if (matchPageCountdownDisplay) { // Reinicia o display se o elemento existir
                matchPageCountdownDisplay.textContent = "00:00";
            }
            countdownMinutesInput.value = 0;
            countdownSecondsInput.value = 0;
            startCountdownBtn.disabled = false;
            pauseCountdownBtn.disabled = true;
            countdownMinutesInput.disabled = false;
            countdownSecondsInput.disabled = false;
            saveData();
        }

        // Adiciona event listeners para os botões do temporizador regressivo
        startCountdownBtn.addEventListener('click', startCountdown);
        pauseCountdownBtn.addEventListener('click', pauseCountdown);
        resetCountdownBtn.addEventListener('click', resetCountdown);

        // Atualiza countdownRemainingTime quando os inputs mudam (apenas se não estiver rodando)
        countdownMinutesInput.addEventListener('input', () => {
            if (!isCountdownRunning) {
                countdownRemainingTime = (parseInt(countdownMinutesInput.value, 10) || 0) * 60 * 1000 + (parseInt(countdownSecondsInput.value, 10) || 0) * 1000;
                updateCountdownDisplay();
            }
        });
        countdownSecondsInput.addEventListener('input', () => {
            if (!isCountdownRunning) {
                countdownRemainingTime = (parseInt(countdownMinutesInput.value, 10) || 0) * 60 * 1000 + (parseInt(countdownSecondsInput.value, 10) || 0) * 1000;
                updateCountdownDisplay();
            }
        });


        // --- Funções Principais do Placar Geral ---
        function calculateTotal(teamData) {
            let total = 0;
            if (teamData.scores) {
                for (const modalityId in teamData.scores) {
                    total += parseInt(teamData.scores[modalityId] || 0);
                }
            }
            return total;
        }

        /**
         * Renderiza uma única linha de equipe no placar principal.
         * @param {object} team - Os dados da equipe a ser renderizada.
         */
        function renderTeamRow(team) {
            const row = document.createElement('div');
            row.className = 'grid-row';
            row.dataset.id = team.id;

            const numModalityColumns = allModalities.length;
            row.style.gridTemplateColumns = `1.5fr repeat(${numModalityColumns}, 1fr) 1fr 0.75fr`;

            let modalityInputsHtml = '';
            allModalities.forEach(modality => {
                const score = team.scores ? (team.scores[modality.id] || 0) : 0;
                modalityInputsHtml += `
                    <div class="grid-cell">
                        <input type="number" class="score-input" data-modality-id="${modality.id}" value="${score}" title="Pontuação para ${modality.name}">
                    </div>
                `;
            });

            row.innerHTML = `
                <div class="grid-cell team-name-cell">
                    <span class="team-name-display">${team.name}</span>
                    <input type="text" class="team-name-input w-full hidden" value="${team.name}" placeholder="Nome da Equipe" maxlength="30" title="Nome da Equipe">
                </div>
                ${modalityInputsHtml}
                <div class="grid-cell total-score">${team.total || 0}</div>
                <div class="grid-cell relative flex flex-col items-center justify-center gap-1">
                    <button class="edit-team-btn w-full" title="Editar Turma">Editar</button>
                    <button class="remove-team-btn w-full" title="Remover Turma">Remover</button>
                    <span class="save-feedback absolute right-0 top-1/2 -translate-y-1/2">✔ Salvo!</span>
                </div>
            `;
            scoreboardBody.appendChild(row);

            const teamNameDisplay = row.querySelector('.team-name-display');
            const teamNameInput = row.querySelector('.team-name-input');
            const editButton = row.querySelector('.edit-team-btn');
            const removeButton = row.querySelector('.remove-team-btn');

            const scoreInputs = row.querySelectorAll('.score-input');
            scoreInputs.forEach(input => {
                let timeoutId;
                input.addEventListener('input', () => {
                    clearTimeout(timeoutId);
                    timeoutId = setTimeout(() => {
                        updateTeamScore(team.id, row);
                    }, 500);
                });
            });

            if (editButton) {
                editButton.addEventListener('click', () => {
                    teamNameDisplay.classList.add('hidden');
                    teamNameInput.classList.remove('hidden');
                    teamNameInput.focus();
                });
            }

            if (removeButton) {
                removeButton.addEventListener('click', () => {
                    showConfirmationModal('Tem certeza que deseja remover esta turma? Esta ação é irreversível.', () => {
                        deleteTeam(team.id);
                    });
                });
            }

            const saveTeamName = () => {
                const newName = teamNameInput.value.trim();
                if (newName && newName !== teamNameDisplay.textContent) {
                    updateTeamScore(team.id, row);
                }
                teamNameDisplay.textContent = teamNameInput.value;
                teamNameDisplay.classList.remove('hidden');
                teamNameInput.classList.add('hidden');
            };

            teamNameInput.addEventListener('blur', saveTeamName);
            teamNameInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    saveTeamName();
                }
            });
        }

        /**
         * Atualiza a pontuação de uma equipe na matriz global e re-renderiza o placar.
         * @param {string} teamId - O ID da equipe a ser atualizada.
         * @param {HTMLElement} rowElement - O elemento da linha HTML da equipe.
         */
        function updateTeamScore(teamId, rowElement) {
            const teamIndex = allTeams.findIndex(t => t.id === teamId);
            if (teamIndex === -1) {
                showStatusMessage("Erro: Turma não encontrada.", 'error');
                return;
            }

            const teamName = rowElement.querySelector('.team-name-input').value;
            const updatedScores = {};
            rowElement.querySelectorAll('.score-input').forEach(input => {
                const modalityId = input.dataset.modalityId;
                updatedScores[modalityId] = parseInt(input.value) || 0;
            });

            const newTeamData = {
                id: teamId,
                name: teamName,
                scores: updatedScores,
            };
            newTeamData.total = calculateTotal(newTeamData);

            allTeams[teamIndex] = newTeamData;
            saveData();
            renderScoreboard(); // Re-renderiza todo o placar para atualizar totais e ordem

            const updatedRowElement = scoreboardBody.querySelector(`[data-id="${teamId}"]`);
            if (updatedRowElement) {
                const saveFeedback = updatedRowElement.querySelector('.save-feedback');
                if (saveFeedback) {
                     saveFeedback.classList.add('visible');
                     setTimeout(() => {
                         saveFeedback.classList.remove('visible');
                     }, 1500);
                }
            }
        }

        // Event listener para adicionar uma nova turma
        addTeamBtn.addEventListener('click', () => {
            const newTeamId = generateUniqueId();
            const initialScores = {};
            allModalities.forEach(modality => {
                initialScores[modality.id] = 0;
            });

            const newTeam = {
                id: newTeamId,
                name: `Nova Equipe ${allTeams.length + 1}`,
                scores: initialScores,
                total: 0,
            };
            allTeams.push(newTeam);
            saveData();
            renderScoreboard();
            showStatusMessage("Nova turma adicionada com sucesso!");
        });

        /**
         * Exclui uma equipe da matriz global e re-renderiza o placar.
         * @param {string} teamId - O ID da equipe a ser excluída.
         */
        function deleteTeam(teamId) {
            allTeams = allTeams.filter(team => team.id !== teamId);
            saveData();
            renderScoreboard();
            showStatusMessage("Turma eliminada com sucesso!");
        }

        // Event listener para reiniciar todas as pontuações
        resetScoresBtn.addEventListener('click', () => {
            showConfirmationModal('Tem certeza que deseja reiniciar todas as pontuações para zero? Esta ação é irreversível.', () => {
                allTeams.forEach(team => {
                    for (const modalityId in team.scores) {
                        team.scores[modalityId] = 0;
                    }
                    team.total = calculateTotal(team);
                });
                saveData();
                renderScoreboard();
                showStatusMessage("Todas as pontuações foram reiniciadas com sucesso!");
            });
        });

        // --- Funções de Gerenciamento de Modalidades ---
        function addModality() {
            const modalityName = newModalityNameInput.value.trim();
            if (!modalityName) {
                showStatusMessage("O nome da modalidade não pode estar vazio.", 'error');
                return;
            }
            if (allModalities.some(m => m.name.toLowerCase() === modalityName.toLowerCase())) {
                showStatusMessage("Uma modalidade com este nome já existe.", 'error');
                return;
            }

            const newModalityId = generateUniqueId();
            const newModality = {
                id: newModalityId,
                name: modalityName,
                order: allModalities.length + 1,
            };
            allModalities.push(newModality);
            allModalities.sort((a,b) => a.order - b.order);
            saveData();
            renderCurrentModalities();

            allTeams.forEach(team => {
                team.scores[newModalityId] = 0;
                team.total = calculateTotal(team);
            });
            renderScoreboard(); // Re-renderiza o placar com a nova coluna
            showStatusMessage(`Modalidade "${modalityName}" adicionada com sucesso!`);
            newModalityNameInput.value = '';
        }

        function updateModality(modalityId, newName) {
            const trimmedName = newName.trim();
            if (!trimmedName) {
                showStatusMessage("O nome da modalidade não pode estar vazio.", 'error');
                return;
            }
            if (allModalities.some(m => m.id !== modalityId && m.name.toLowerCase() === trimmedName.toLowerCase())) {
                showStatusMessage("Uma modalidade com este nome já existe.", 'error');
                return;
            }

            const modalityIndex = allModalities.findIndex(m => m.id === modalityId);
            if (modalityIndex !== -1) {
                allModalities[modalityIndex].name = trimmedName;
                saveData();
                renderCurrentModalities();
                renderScoreboard(); // Re-renderiza o cabeçalho e as linhas das equipes
                showStatusMessage(`Modalidade atualizada para "${trimmedName}" com sucesso!`);
            }
        }

        function deleteModality(modalityId, modalityName) {
            showConfirmationModal(`Tem certeza que deseja excluir a modalidade "${modalityName}"? Isso removerá todas as pontuações associadas a ela para todas as turmas.`, () => {
                allModalities = allModalities.filter(modality => modality.id !== modalityId);
                saveData();
                renderCurrentModalities();

                allTeams.forEach(team => {
                    if (team.scores.hasOwnProperty(modalityId)) {
                        delete team.scores[modalityId];
                    }
                    team.total = calculateTotal(team);
                });
                renderScoreboard(); // Re-renderiza o placar sem a coluna da modalidade excluída
                showStatusMessage(`Modalidade "${modalityName}" eliminada com sucesso!`);
            });
        }

        addModalityBtn.addEventListener('click', addModality);

        /**
         * Renderiza as modalidades atuais como tags no gerenciador.
         */
        function renderCurrentModalities() {
            currentModalitiesContainer.innerHTML = '';
            allModalities.forEach(modality => {
                const tag = document.createElement('span');
                tag.className = 'modality-tag';
                tag.dataset.modalityId = modality.id;

                const nameDisplay = document.createElement('span');
                nameDisplay.className = 'modality-name-display';
                nameDisplay.textContent = modality.name;
                tag.appendChild(nameDisplay);

                const editBtn = document.createElement('button');
                editBtn.className = 'modality-action-btn';
                editBtn.title = 'Editar Modalidade';
                editBtn.textContent = 'Editar';
                editBtn.dataset.modalityId = modality.id;
                tag.appendChild(editBtn);

                const deleteBtn = document.createElement('button');
                deleteBtn.className = 'modality-action-btn';
                deleteBtn.title = 'Excluir Modalidade';
                deleteBtn.textContent = 'Excluir';
                deleteBtn.dataset.modalityId = modality.id;
                deleteBtn.dataset.modalityName = modality.name;
                tag.appendChild(deleteBtn);

                currentModalitiesContainer.appendChild(tag);

                editBtn.addEventListener('click', () => {
                    if (document.querySelector('.modality-tag.editing')) {
                        showStatusMessage("Já está a editar outra modalidade. Salve ou cancele primeiro.", "status");
                        return;
                    }

                    tag.classList.add('editing');

                    const input = document.createElement('input');
                    input.type = 'text';
                    input.className = 'modality-name-input';
                    input.value = nameDisplay.textContent;
                    input.maxLength = 20;
                    input.title = 'Editar Nome da Modalidade';

                    tag.replaceChild(input, nameDisplay);
                    input.focus();

                    editBtn.classList.add('hidden');
                    deleteBtn.classList.add('hidden');

                    const saveChanges = () => {
                        const newName = input.value.trim();
                        if (newName && newName !== modality.name) {
                            updateModality(modality.id, newName);
                        } else {
                            tag.classList.remove('editing');
                            tag.replaceChild(nameDisplay, input);
                            nameDisplay.textContent = modality.name;
                            editBtn.classList.remove('hidden');
                            deleteBtn.classList.remove('hidden');
                        }
                    };

                    input.addEventListener('blur', saveChanges);
                    input.addEventListener('keypress', (e) => {
                        if (e.key === 'Enter') {
                            input.blur();
                        }
                    });
                });

                deleteBtn.addEventListener('click', (event) => {
                    const modalityId = event.target.dataset.modalityId;
                    const modalityName = event.target.dataset.modalityName;
                    deleteModality(modalityId, modalityName);
                });
            });
        }

        /**
         * Renderiza todo o placar principal com base nos dados locais.
         */
        function renderScoreboard() {
            loadingIndicator.classList.add('hidden');

            scoreboardBody.innerHTML = '';
            gridHeader.innerHTML = '';

            const numModalityColumns = allModalities.length;
            gridHeader.style.gridTemplateColumns = `1.5fr repeat(${numModalityColumns}, 1fr) 1fr 0.75fr`;
            gridHeader.innerHTML = `
                <div class="grid-cell header-orange-text">EQUIPES</div>
                ${allModalities.map(modality => `<div class="grid-cell header-orange-text">${modality.name}</div>`).join('')}
                <div class="grid-cell header-orange-text">TOTAL</div>
                <div class="grid-cell"></div> `;

            allTeams.sort((a, b) => b.total - a.total);

            if (allTeams.length === 0) {
                emptyStateMessage.classList.remove('hidden');
            } else {
                emptyStateMessage.classList.add('hidden');
                allTeams.forEach(team => {
                    renderTeamRow(team);
                });
            }
        }

        // --- Funções da Página de Seleção de Modalidades ---
        function renderModalitiesPage() {
            modalityListContainer.innerHTML = ''; // Limpa botões anteriores

            if (allModalities.length === 0) {
                noModalitiesMessage.classList.remove('hidden');
            } else {
                noModalitiesMessage.classList.add('hidden');
                allModalities.forEach(modality => {
                    const button = document.createElement('button');
                    button.className = 'modality-button';
                    button.textContent = modality.name;
                    button.dataset.modalityId = modality.id; // Armazena o ID para navegação
                    button.addEventListener('click', () => {
                        renderDetailedScoreboardPage(modality.id);
                        showPage('detailedScoreboardPage'); // Navega para a página de detalhes
                    });
                    modalityListContainer.appendChild(button);
                });
            }
        }

        // Event listener para o botão "Placar por Modalidade" (Página Principal -> Página de Modalidades)
        viewModalityScoresBtn.addEventListener('click', () => {
            renderModalitiesPage(); // Renderiza os botões de modalidade
            showPage('modalitiesPage'); // Mostra a página de seleção de modalidades
        });

        // Event listener para o botão "Voltar" na Página de Seleção de Modalidades
        modalitiesPageBackButton.addEventListener('click', () => {
            showPage('mainScoreboardPage'); // Volta para o placar principal
        });


        // --- Funções da Página de Placar Detalhado ---
        /**
         * Renderiza a página de placar detalhado para uma modalidade específica.
         * @param {string} modalityId - O ID da modalidade a ser exibida.
         */
        function renderDetailedScoreboardPage(modalityId) {
            modalityNameDisplay.textContent = "";
            detailedScoresContainer.innerHTML = '';
            noScoresMessage.classList.add('hidden');
            modalitySpecificMatchesContainer.innerHTML = ''; // Limpa confrontos anteriores
            noModalityMatchesMessage.classList.add('hidden');

            if (!modalityId) {
                modalityNameDisplay.textContent = "Modalidade não encontrada.";
                noScoresMessage.classList.remove('hidden');
                noModalityMatchesMessage.classList.remove('hidden');
                return;
            }

            const selectedModality = allModalities.find(m => m.id === modalityId);

            if (selectedModality) {
                modalityNameDisplay.textContent = `Placar de ${selectedModality.name}`;

                const teamsWithScores = allTeams
                    .filter(team => team.scores && team.scores.hasOwnProperty(modalityId))
                    .map(team => ({
                        name: team.name,
                        score: parseInt(team.scores[modalityId]) || 0
                    }))
                    .sort((a, b) => b.score - a.score); // Ordena pela pontuação em ordem decrescente

                if (teamsWithScores.length === 0) {
                    noScoresMessage.classList.remove('hidden');
                } else {
                    teamsWithScores.forEach(team => {
                        const scoreItem = document.createElement('div');
                        scoreItem.className = 'score-item';
                        scoreItem.innerHTML = `
                            <span class="team-name">${team.name}</span>
                            <span class="team-score">${team.score}</span>
                        `;
                        detailedScoresContainer.appendChild(scoreItem);
                    });
                }

                // Renderiza confrontos ativos para esta modalidade
                renderModalitySpecificMatches(modalityId);

            } else {
                modalityNameDisplay.textContent = "Modalidade desconhecida.";
                noScoresMessage.classList.remove('hidden');
                noModalityMatchesMessage.classList.remove('hidden');
            }
        }

        /**
         * Renderiza os confrontos ativos para uma modalidade específica.
         * @param {string} modalityId - O ID da modalidade.
         */
        function renderModalitySpecificMatches(modalityId) {
            modalitySpecificMatchesContainer.innerHTML = '';
            const matchesForModality = activeMatches.filter(match => match.modalityId === modalityId);

            if (matchesForModality.length === 0) {
                noModalityMatchesMessage.classList.remove('hidden');
            } else {
                noModalityMatchesMessage.classList.add('hidden');
                matchesForModality.forEach(match => {
                    const team1 = allTeams.find(t => t.id === match.team1Id);
                    const team2 = allTeams.find(t => t.id === match.team2Id);

                    if (!team1 || !team2) {
                        console.error("Equipe não encontrada para o confronto da modalidade:", match);
                        return;
                    }

                    const matchItem = document.createElement('div');
                    matchItem.className = 'match-item'; // Reutiliza estilo de match-item
                    matchItem.innerHTML = `
                        <div class="text-lg font-semibold text-gray-700 mb-2">Confronto:</div>
                        <div class="match-teams-display">
                            <div class="match-team-block">
                                <span class="match-team-name">${team1.name}</span>
                                <span class="match-score-input">${match.score1}</span>
                            </div>
                            <span class="match-vs-text">vs.</span>
                            <div class="match-team-block">
                                <span class="match-team-name">${team2.name}</span>
                                <span class="match-score-input">${match.score2}</span>
                            </div>
                        </div>
                    `;
                    modalitySpecificMatchesContainer.appendChild(matchItem);
                });
            }
        }


        // Event listener para o botão "Voltar" na Página de Placar Detalhado
        detailedPageBackButton.addEventListener('click', () => {
            renderModalitiesPage(); // Re-renderiza a lista de modalidades
            showPage('modalitiesPage'); // Volta para a seleção de modalidades
        });

        // Event listener para o botão "Voltar ao Início" na Página de Placar Detalhado
        detailedPageHomeButton.addEventListener('click', () => {
            showPage('mainScoreboardPage'); // Volta para o placar principal
        });


        // --- Funções da Nova Página de Confrontos de Equipes ---

        /**
         * Popula os seletores de equipes para criar um novo confronto.
         */
        function populateTeamSelectors() {
            team1Select.innerHTML = '<option value="">Selecione Equipe 1</option>';
            team2Select.innerHTML = '<option value="">Selecione Equipe 2</option>';

            if (allTeams.length === 0) {
                showStatusMessage("Nenhuma equipe cadastrada. Por favor, adicione equipes na página principal.", 'error');
                return;
            }

            allTeams.forEach(team => {
                const option1 = document.createElement('option');
                option1.value = team.id;
                option1.textContent = team.name;
                team1Select.appendChild(option1);

                const option2 = document.createElement('option');
                option2.value = team.id;
                option2.textContent = team.name;
                team2Select.appendChild(option2);
            });
        }

        /**
         * Popula o seletor de modalidade para criar um novo confronto.
         */
        function populateMatchModalitySelector() {
            matchModalitySelect.innerHTML = '<option value="">Selecione a Modalidade</option>';
            if (allModalities.length === 0) {
                showStatusMessage("Nenhuma modalidade cadastrada. Por favor, adicione modalidades na página principal.", 'error');
                return;
            }
            allModalities.forEach(modality => {
                const option = document.createElement('option');
                option.value = modality.id;
                option.textContent = modality.name;
                matchModalitySelect.appendChild(option);
            });
        }

        /**
         * Cria um novo confronto entre duas equipes e uma modalidade selecionadas.
         */
        startNewMatchBtn.addEventListener('click', () => {
            const team1Id = team1Select.value;
            const team2Id = team2Select.value;
            const modalityId = matchModalitySelect.value; // Obtém o ID da modalidade selecionada

            if (!team1Id || !team2Id || !modalityId) { // Adiciona verificação de modalityId
                showStatusMessage("Por favor, selecione ambas as equipes e a modalidade para o confronto.", 'error');
                return;
            }

            if (team1Id === team2Id) {
                showStatusMessage("As equipes devem ser diferentes para um confronto.", 'error');
                return;
            }

            // Verifica se este confronto (equipes + modalidade) já existe
            const existingMatch = activeMatches.some(match =>
                ((match.team1Id === team1Id && match.team2Id === team2Id) ||
                 (match.team1Id === team2Id && match.team2Id === team1Id)) &&
                match.modalityId === modalityId // Verifica a modalidade também
            );

            if (existingMatch) {
                showStatusMessage("Este confronto nesta modalidade já está ativo.", 'status');
                return;
            }

            const newMatch = {
                id: generateUniqueId(),
                team1Id: team1Id,
                team2Id: team2Id,
                modalityId: modalityId, // Armazena o ID da modalidade
                score1: 0,
                score2: 0
            };
            activeMatches.push(newMatch);
            saveData();
            renderMatchScoreboardPage();
            const selectedModalityName = allModalities.find(m => m.id === modalityId)?.name || 'Desconhecida';
            showStatusMessage(`Confronto de ${selectedModalityName} entre ${allTeams.find(t => t.id === team1Id).name} e ${allTeams.find(t => t.id === team2Id).name} iniciado!`);

            // Reseta seletores
            team1Select.value = "";
            team2Select.value = "";
            matchModalitySelect.value = ""; // Reseta o seletor de modalidade
        });

        /**
         * Atualiza a pontuação de uma equipe em um confronto ativo.
         * @param {string} matchId - O ID do confronto.
         * @param {string} teamNumber - 'team1' ou 'team2' para indicar qual equipe foi atualizada.
         * @param {number} newScore - A nova pontuação.
         */
        function updateMatchScore(matchId, teamNumber, newScore) {
            const matchIndex = activeMatches.findIndex(m => m.id === matchId);
            if (matchIndex === -1) {
                console.error("Confronto não encontrado para atualização de placar:", matchId);
                return;
            }

            if (teamNumber === 'team1') {
                activeMatches[matchIndex].score1 = newScore;
            } else if (teamNumber === 'team2') {
                activeMatches[matchIndex].score2 = newScore;
            }
            saveData();
            // Re-renderiza apenas o confronto específico para feedback mais rápido, ou todo se preferir
            renderMatchScoreboardPage(); // Re-renderiza todos os confrontos para simplicidade
        }

        /**
         * Encerra e remove um confronto ativo.
         * @param {string} matchId - O ID do confronto a ser encerrado.
         */
        function endMatch(matchId) {
            showConfirmationModal('Tem certeza que deseja encerrar este confronto? Esta ação é irreversível.', () => {
                activeMatches = activeMatches.filter(match => match.id !== matchId);
                saveData();
                renderMatchScoreboardPage();
                showStatusMessage("Confronto encerrado com sucesso!");
            });
        }

        /**
         * Renderiza todos os confrontos ativos na página de confrontos.
         */
        function renderMatchScoreboardPage() {
            activeMatchesContainer.innerHTML = ''; // Limpa confrontos anteriores

            if (activeMatches.length === 0) {
                noActiveMatchesMessage.classList.remove('hidden');
            } else {
                noActiveMatchesMessage.classList.add('hidden');
                activeMatches.forEach(match => {
                    const team1 = allTeams.find(t => t.id === match.team1Id);
                    const team2 = allTeams.find(t => t.id === match.team2Id);
                    const modality = allModalities.find(m => m.id === match.modalityId); // Obtém o objeto da modalidade

                    if (!team1 || !team2 || !modality) { // Verifica se a modalidade existe
                        console.error("Equipe ou modalidade não encontrada para o confronto:", match);
                        return; // Pula confrontos com equipes inválidas
                    }

                    const matchItem = document.createElement('div');
                    matchItem.className = 'match-item';
                    matchItem.dataset.matchId = match.id;

                    matchItem.innerHTML = `
                        <button class="end-match-btn" title="Encerrar Confronto">X</button>
                        <div class="text-lg font-semibold text-gray-700 mb-2">${modality.name}</div> <!-- Exibe o nome da modalidade -->
                        <div class="match-teams-display">
                            <div class="match-team-block">
                                <span class="match-team-name">${team1.name}</span>
                                <input type="number" class="match-score-input" data-team-number="team1" value="${match.score1}" min="0">
                            </div>
                            <span class="match-vs-text">vs.</span>
                            <div class="match-team-block">
                                <span class="match-team-name">${team2.name}</span>
                                <input type="number" class="match-score-input" data-team-number="team2" value="${match.score2}" min="0">
                            </div>
                        </div>
                    `;
                    activeMatchesContainer.appendChild(matchItem);

                    // Adiciona event listeners para os inputs de placar
                    const scoreInputs = matchItem.querySelectorAll('.match-score-input');
                    scoreInputs.forEach(input => {
                        let timeoutId;
                        input.addEventListener('input', () => {
                            clearTimeout(timeoutId);
                            timeoutId = setTimeout(() => {
                                const teamNumber = input.dataset.teamNumber;
                                const newScore = parseInt(input.value) || 0;
                                updateMatchScore(match.id, teamNumber, newScore);
                            }, 300); // Debounce para evitar muitas atualizações rápidas
                        });
                    });

                    // Adiciona event listener para o botão de encerrar confronto
                    matchItem.querySelector('.end-match-btn').addEventListener('click', () => {
                        endMatch(match.id);
                    });
                });
            }
        }

        // Event listener para o botão "Gerenciar Confrontos" (Página Principal -> Página de Confrontos)
        viewMatchesBtn.addEventListener('click', () => {
            showPage('matchScoreboardPage');
        });

        // Event listener para o botão "Voltar" na Página de Confrontos
        matchScoreboardPageBackButton.addEventListener('click', () => {
            showPage('mainScoreboardPage'); // Volta para o placar principal
        });

        // Event listener para o botão "Voltar ao Início" na Página de Confrontos
        matchScoreboardPageHomeButton.addEventListener('click', () => {
            showPage('mainScoreboardPage'); // Volta para o placar principal
        });

        // --- Funcionalidade de Relatório de Impressão ---
        printReportBtn.addEventListener('click', generatePrintReport);

        function generatePrintReport() {
            let reportContent = `
                <div class="print-hide" style="text-align: center; margin-bottom: 20px;">
                    <button onclick="window.print()" style="padding: 10px 20px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer;">Imprimir</button>
                    <button onclick="document.getElementById('printContainer').style.display='none'; document.body.classList.remove('printing-active');" style="padding: 10px 20px; background-color: #6c757d; color: white; border: none; border-radius: 5px; cursor: pointer; margin-left: 10px;">Fechar</button>
                </div>
                <h1 style="text-align: center; color: #1a202c; font-size: 2.5rem; margin-bottom: 20px; padding-bottom: 10px; border-bottom: 2px solid #ccc;">Relatório de Jogos - SENAC PAULISTA</h1>
            `;

            // Adiciona o Placar Principal ao relatório
            reportContent += `<h2 style="color: #2196F3; font-size: 1.8rem; margin-top: 30px; margin-bottom: 15px; text-align: center;">Placar Geral de Turmas</h2>`;
            if (allTeams.length > 0) {
                const numModalityColumns = allModalities.length;
                reportContent += `
                    <div style="display: grid; grid-template-columns: 1.5fr repeat(${numModalityColumns}, 1fr) 1fr; gap: 8px; background-color: #2196F3; color: white; font-weight: 700; padding: 12px 8px; border-radius: 8px; margin-bottom: 12px; border: 1px solid #1976D2;">
                        <div style="text-align: center; color: #FF9800;">EQUIPES</div>
                        ${allModalities.map(modality => `<div style="text-align: center; color: #FF9800;">${modality.name}</div>`).join('')}
                        <div style="text-align: center; color: #FF9800;">TOTAL</div>
                    </div>
                `;
                allTeams.sort((a, b) => b.total - a.total).forEach((team, index) => {
                    const rowBgColor = index % 2 === 0 ? '#E3F2FD' : '#D1E6FA'; // Alternating row colors
                    reportContent += `
                        <div style="display: grid; grid-template-columns: 1.5fr repeat(${numModalityColumns}, 1fr) 1fr; gap: 8px; padding: 12px 0; align-items: center; text-align: center; background-color: ${rowBgColor}; border-radius: 8px; margin-bottom: 5px; border: 1px solid #ccc;">
                            <div style="padding: 8px; text-align: left; padding-left: 12px; font-weight: 700; color: #333333;">${team.name}</div>
                            ${allModalities.map(modality => `<div style="padding: 8px; background-color: ${rowBgColor}; color: #333333;">${team.scores ? (team.scores[modality.id] || 0) : 0}</div>`).join('')}
                            <div style="padding: 8px; font-weight: 700; color: #333333; background-color: #FFECB3;">${team.total || 0}</div>
                        </div>
                    `;
                });
            } else {
                reportContent += `<p style="text-align: center; color: #6b7280; margin-top: 20px; font-style: italic;">Nenhuma turma cadastrada.</p>`;
            }

            // Adiciona Confrontos ao relatório
            reportContent += `<h2 style="color: #2196F3; font-size: 1.8rem; margin-top: 40px; margin-bottom: 15px; text-align: center;">Confrontos Ativos</h2>`;
            if (activeMatches.length > 0) {
                activeMatches.forEach(match => {
                    const team1 = allTeams.find(t => t.id === match.team1Id);
                    const team2 = allTeams.find(t => t.id === match.team2Id);
                    const modality = allModalities.find(m => m.id === match.modalityId);

                    if (team1 && team2 && modality) {
                        reportContent += `
                            <div style="background-color: #D1E6FA; padding: 20px; border-radius: 12px; margin-bottom: 15px; display: flex; flex-wrap: wrap; justify-content: space-around; align-items: center; border: 1px solid #90CAF9;">
                                <div style="width: 100%; text-align: center; font-size: 1.2rem; font-weight: 600; color: #333; margin-bottom: 10px;">Modalidade: ${modality.name}</div>
                                <div style="display: flex; flex-direction: column; align-items: center; flex: 1; min-width: 100px;">
                                    <span style="font-size: 1.5rem; font-weight: 700; color: #333; text-align: center;">${team1.name}</span>
                                    <span style="font-size: 2.5rem; font-weight: 800; color: #FF9800; background-color: #FFF3E0; padding: 5px 15px; border-radius: 8px; margin-top: 5px;">${match.score1}</span>
                                </div>
                                <span style="font-size: 1.8rem; font-weight: 700; color: #2196F3; margin: 0 15px;">vs.</span>
                                <div style="display: flex; flex-direction: column; align-items: center; flex: 1; min-width: 100px;">
                                    <span style="font-size: 1.5rem; font-weight: 700; color: #333; text-align: center;">${team2.name}</span>
                                    <span style="font-size: 2.5rem; font-weight: 800; color: #FF9800; background-color: #FFF3E0; padding: 5px 15px; border-radius: 8px; margin-top: 5px;">${match.score2}</span>
                                </div>
                            </div>
                        `;
                    }
                });
            } else {
                reportContent += `<p style="text-align: center; color: #6b7280; margin-top: 20px; font-style: italic;">Nenhum confronto ativo.</p>`;
            }

            // Adiciona Placares por Modalidade ao relatório
            reportContent += `<h2 style="color: #2196F3; font-size: 1.8rem; margin-top: 40px; margin-bottom: 15px; text-align: center;">Placares por Modalidade</h2>`;
            if (allModalities.length > 0) {
                allModalities.forEach(modality => {
                    reportContent += `
                        <h3 style="font-size: 1.5rem; font-weight: 600; color: #333; margin-top: 20px; margin-bottom: 10px; text-align: center; border-bottom: 1px solid #eee; padding-bottom: 5px;">Modalidade: ${modality.name}</h3>
                    `;
                    const teamsWithModalityScores = allTeams
                        .filter(team => team.scores && team.scores.hasOwnProperty(modality.id))
                        .map(team => ({
                            name: team.name,
                            score: parseInt(team.scores[modality.id]) || 0
                        }))
                        .sort((a, b) => b.score - a.score);

                    if (teamsWithModalityScores.length > 0) {
                        teamsWithModalityScores.forEach(team => {
                            reportContent += `
                                <div style="display: flex; justify-content: space-between; align-items: center; background-color: #E3F2FD; padding: 15px 25px; margin-bottom: 8px; border-radius: 8px; border: 1px solid #90CAF9;">
                                    <span style="font-size: 1.2rem; font-weight: 600; color: #333;">${team.name}</span>
                                    <span style="font-size: 1.8rem; font-weight: 800; color: #FF9800;">${team.score}</span>
                                </div>
                            `;
                        });
                    } else {
                        reportContent += `<p style="text-align: center; color: #6b7280; margin-top: 10px; font-style: italic;">Nenhum placar para esta modalidade.</p>`;
                    }
                });
            } else {
                reportContent += `<p style="text-align: center; color: #6b7280; margin-top: 20px; font-style: italic;">Nenhuma modalidade cadastrada.</p>`;
            }

            // Exibe o relatório no contêiner oculto e dispara a impressão
            printContainer.innerHTML = reportContent;
            printContainer.style.display = 'block';
            document.body.classList.add('printing-active'); // Adiciona classe ao corpo para ocultar outros elementos durante a impressão

            window.print();

            // Oculta o contêiner de impressão após o fechamento da caixa de diálogo de impressão
            // Usando um pequeno atraso, pois print() é bloqueante
            setTimeout(() => {
                printContainer.style.display = 'none';
                document.body.classList.remove('printing-active');
            }, 100);
        }

        // --- Carregamento Inicial da Aplicação ---
        document.addEventListener('DOMContentLoaded', () => {
            loadData(); // Carrega todos os dados (equipes, modalidades, temporizadores, confrontos)
            renderScoreboard(); // Renderiza o placar principal inicialmente
            renderCurrentModalities(); // Renderiza as tags de modalidade na seção do gerenciador
            showPage('mainScoreboardPage'); // Garante que a página principal seja mostrada no carregamento
        });
    </script>
</body>
</html>
