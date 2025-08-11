# 🏥 Calculadora de IMC

**Especificações Técnicas Obrigatórias**

Desenvolver uma aplicação web simples que permita ao usuário calcular seu Índice de Massa Corporal (IMC) e obter classificações baseadas nos padrões da OMS. Este foi meu primeiro projeto utilizando conceitos fundamentais de desenvolvimento web, evoluindo de uma implementação em linguagem C para uma versão web interativa.

## 🎯 **Objetivo**

Criar uma calculadora de IMC intuitiva e responsiva que:
- Calcule o IMC com base no peso e altura informados
- Forneça classificação automática segundo padrões da Organização Mundial da Saúde
- Apresente recomendações personalizadas para cada faixa de IMC
- Inclua validação de dados e tratamento de erros
- Ofereça uma interface visual atrativa e fácil de usar

## 🚀 **Tecnologias utilizadas:**

- **HTML5:** estruturação semântica da aplicação
- **CSS3:** estilização avançada com gradients, flexbox e animações
- **JavaScript (ES6+):** lógica de negócio e interatividade
- **Responsive Design:** adaptação para diferentes dispositivos

## 🎓 **O que aprendi:**

### **Lógica de Programação:**
- **Estruturas condicionais:** implementação de múltiplas condições `if/else if` para classificar faixas de IMC
- **Validação de entrada:** verificação de dados do usuário para prevenir erros e garantir valores válidos
- **Cálculos matemáticos:** aplicação da fórmula IMC = peso ÷ (altura²) com precisão decimal

### **Manipulação do DOM:**
- **Seleção de elementos:** utilização de `getElementById()` para acessar inputs e divs específicas
- **Eventos:** captura de cliques de botão e teclas pressionadas (`addEventListener`)
- **Atualização dinâmica:** modificação de conteúdo e estilos em tempo real sem recarregar a página

### **Interface e Experiência do Usuário:**
- **Design responsivo:** criação de layout que se adapta a diferentes tamanhos de tela
- **Feedback visual:** implementação de mensagens de erro e sucesso com cores diferenciadas
- **Acessibilidade:** uso de labels apropriadas e navegação por teclado

### **Boas Práticas de Desenvolvimento:**
- **Separação de responsabilidades:** organização clara entre HTML (estrutura), CSS (apresentação) e JavaScript (comportamento)
- **Tratamento de erros:** implementação de validações robustas com mensagens informativas
- **Código limpo:** uso de nomes descritivos para variáveis e funções, comentários explicativos

### **Evolução de C para Web:**
- **Migração de conceitos:** adaptação da lógica implementada em C para JavaScript
- **Entrada de dados:** transição de `scanf()` para formulários HTML interativos
- **Saída de dados:** substituição de `printf()` por manipulação dinâmica do DOM

## 📊 **Funcionalidades Implementadas:**

✅ Cálculo preciso do IMC com validação de entrada  
✅ Classificação automática em 6 categorias (OMS)  
✅ Recomendações personalizadas por faixa  
✅ Tabela de referência visual  
✅ Design moderno com gradientes e animações  
✅ Responsividade para mobile e desktop  
✅ Tratamento de erros com feedback visual  

## 🔧 **Como executar:**

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de IMC</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            max-width: 500px;
            width: 100%;
            text-align: center;
        }
        
        .title {
            color: #333;
            margin-bottom: 10px;
            font-size: 2.2em;
        }
        
        .subtitle {
            color: #666;
            margin-bottom: 30px;
            font-size: 1.1em;
        }
        
        .input-group {
            margin-bottom: 20px;
            text-align: left;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            color: #333;
            font-weight: bold;
        }
        
        input {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }
        
        input:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            cursor: pointer;
            transition: transform 0.3s ease;
            margin: 20px 0;
        }
        
        .btn:hover {
            transform: translateY(-2px);
        }
        
        .resultado {
            margin-top: 30px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 10px;
            border-left: 5px solid #667eea;
            display: none;
        }
        
        .imc-valor {
            font-size: 2em;
            font-weight: bold;
            color: #333;
            margin-bottom: 10px;
        }
        
        .classificacao {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .recomendacao {
            color: #666;
            font-style: italic;
        }
        
        .tabela {
            margin-top: 30px;
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
        }
        
        .tabela h3 {
            color: #333;
            margin-bottom: 15px;
        }
        
        .tabela-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }
        
        .erro {
            color: #dc3545;
            background: #f8d7da;
            border: 1px solid #f5c6cb;
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            display: none;
        }
        
        /* Cores para diferentes classificações */
        .abaixo { color: #17a2b8; }
        .normal { color: #28a745; }
        .sobrepeso { color: #ffc107; }
        .obesidade1 { color: #fd7e14; }
        .obesidade2 { color: #dc3545; }
        .obesidade3 { color: #6f42c1; }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="title">🏥 Calculadora de IMC</h1>
        <p class="subtitle">Índice de Massa Corporal</p>
        
        <div class="input-group">
            <label for="peso">Peso (kg):</label>
            <input type="number" id="peso" placeholder="Ex: 70.5" step="0.1" min="0">
        </div>
        
        <div class="input-group">
            <label for="altura">Altura (m):</label>
            <input type="number" id="altura" placeholder="Ex: 1.75" step="0.01" min="0">
        </div>
        
        <button class="btn" onclick="calcularIMC()">Calcular IMC</button>
        
        <div id="erro" class="erro"></div>
        
        <div id="resultado" class="resultado">
            <div class="imc-valor" id="imcValor"></div>
            <div class="classificacao" id="classificacao"></div>
            <div class="recomendacao" id="recomendacao"></div>
        </div>
        
        <div class="tabela">
            <h3>📊 Tabela de Referência IMC</h3>
            <div class="tabela-item">
                <span>Abaixo de 18,5</span>
                <span class="abaixo">Abaixo do peso</span>
            </div>
            <div class="tabela-item">
                <span>18,5 a 24,9</span>
                <span class="normal">Peso normal</span>
            </div>
            <div class="tabela-item">
                <span>25,0 a 29,9</span>
                <span class="sobrepeso">Sobrepeso</span>
            </div>
            <div class="tabela-item">
                <span>30,0 a 34,9</span>
                <span class="obesidade1">Obesidade Grau I</span>
            </div>
            <div class="tabela-item">
                <span>35,0 a 39,9</span>
                <span class="obesidade2">Obesidade Grau II</span>
            </div>
            <div class="tabela-item">
                <span>40,0 ou mais</span>
                <span class="obesidade3">Obesidade Grau III</span>
            </div>
        </div>
    </div>

    <script>
        function calcularIMC() {
            // Pega os valores dos inputs (similar ao scanf em C)
            const peso = parseFloat(document.getElementById('peso').value);
            const altura = parseFloat(document.getElementById('altura').value);
            
            // Limpa mensagens anteriores
            document.getElementById('erro').style.display = 'none';
            document.getElementById('resultado').style.display = 'none';
            
            // Validação (similar ao if em C)
            if (!peso || !altura || peso <= 0 || altura <= 0) {
                document.getElementById('erro').textContent = '❌ ERRO: Peso e altura devem ser valores positivos!';
                document.getElementById('erro').style.display = 'block';
                return;
            }
            
            // Calcula IMC (mesma fórmula do C)
            const imc = peso / (altura * altura);
            
            // Determina classificação (similar aos if/else em C)
            let classificacao, recomendacao, classe;
            
            if (imc < 18.5) {
                classificacao = 'ABAIXO DO PESO';
                recomendacao = '💡 Consulte um nutricionista';
                classe = 'abaixo';
            } else if (imc >= 18.5 && imc < 25.0) {
                classificacao = 'PESO NORMAL';
                recomendacao = '✅ Mantenha seus hábitos saudáveis!';
                classe = 'normal';
            } else if (imc >= 25.0 && imc < 30.0) {
                classificacao = 'SOBREPESO';
                recomendacao = '⚠️ Considere uma dieta equilibrada e exercícios';
                classe = 'sobrepeso';
            } else if (imc >= 30.0 && imc < 35.0) {
                classificacao = 'OBESIDADE GRAU I';
                recomendacao = '🏥 Procure orientação médica';
                classe = 'obesidade1';
            } else if (imc >= 35.0 && imc < 40.0) {
                classificacao = 'OBESIDADE GRAU II';
                recomendacao = '🚨 Procure orientação médica urgente';
                classe = 'obesidade2';
            } else {
                classificacao = 'OBESIDADE GRAU III (MÓRBIDA)';
                recomendacao = '🆘 Procure orientação médica imediata';
                classe = 'obesidade3';
            }
            
            // Mostra o resultado (similar ao printf em C)
            document.getElementById('imcValor').textContent = `IMC: ${imc.toFixed(2)}`;
            document.getElementById('classificacao').textContent = classificacao;
            document.getElementById('classificacao').className = `classificacao ${classe}`;
            document.getElementById('recomendacao').textContent = recomendacao;
            document.getElementById('resultado').style.display = 'block';
        }
        
        // Permite calcular pressionando Enter
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                calcularIMC();
            }
        });
    </script>
</body>
</html>

---

*Projeto desenvolvido como exercício prático de desenvolvimento web front-end, demonstrando a evolução de conceitos fundamentais de programação para aplicações interativas.*
