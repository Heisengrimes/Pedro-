<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Coberturas Sugeridas</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

<div>
    <label for="custoVida">Custo de Vida Mensal:</label>
    <input type="number" id="custoVida" placeholder="Digite o custo de vida mensal">
</div>

<div>
    <label for="patrimonio">Patrimônio Aproximado:</label>
    <input type="number" id="patrimonio" placeholder="Digite o patrimônio aproximado">
</div>

<button onclick="calcularCoberturas()">Calcular Coberturas Sugeridas</button>

<div id="resultado"></div>

<script>
    function formatarMoeda(valor) {
        return valor.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
    }

    function calcularCoberturas() {
        const custoVida = parseFloat(document.getElementById('custoVida').value);
        const patrimonio = parseFloat(document.getElementById('patrimonio').value);

        const invalidez = formatarMoeda(custoVida * 100);
        const doencasGraves = formatarMoeda(custoVida * 24);
        const auxilioFuneral = formatarMoeda(10000);
        
        const opcoesDiariasInternacao = [200, 250, 300, 350, 400, 450, 500, 550, 600];
        const diariasInternacao = formatarMoeda(opcoesDiariasInternacao.find(opcao => opcao >= custoVida / 30));

        let vitalicio = formatarMoeda(Math.max(80000, Math.ceil(patrimonio * 0.1 / 10000) * 10000));

        const resultadoHTML = `
            <h2>Coberturas Sugeridas</h2>
            <p>Cobertura de Invalidez: ${invalidez}</p>
            <p>Cobertura de Doenças Graves: ${doencasGraves}</p>
            <p>Cobertura de Auxílio Funeral: ${auxilioFuneral}</p>
            <p>Cobertura de Diárias de Internação Hospitalar: ${diariasInternacao}</p>
            <p>Cobertura Vitalícia: ${vitalicio}</p>
        `;

        document.getElementById('resultado').innerHTML = resultadoHTML;
    }
</script>

</body>
</html>
