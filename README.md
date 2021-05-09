# DADOS-JUROS-
<div id="app"></div>

        <script type="text/javascript" src="http://code.jquery.com/jquery-2.1.3.min.js"></script>
<script type="text/javascript" src="https://assets.moip.com.br/v2/bank-account-validator.min.js"></script>
<script type="text/javascript">
  $(document).ready(function() {
    $("#validate_bank_account").click(function() {
      Moip.BankAccount.validate({
        bankNumber         : $("#bank_number").val(),
        agencyNumber       : $("#agency_number").val(),
        agencyCheckNumber  : $("#agency_check_number").val(),
        accountNumber      : $("#account_number").val(),
        accountCheckNumber : $("#account_check_number").val(),
        valid: function() {
          alert("Conta bancária válida")
        },
        invalid: function(data) {
          var errors = "Conta bancária inválida: \n";
          for(i in data.errors){
            errors += data.errors[i].description + "-" + data.errors[i].code + ")\n";
          }
          alert(errors);
        }
      });
    });
  });
</script> 
<form>
  <select id="bank_number">
    <option value="001">BANCO DO BRASIL S.A.</option>
    <option value="237">BANCO BRADESCO S.A.</option>
    <option value="341">BANCO ITAÚ S.A.</option>
    <option value="104">CAIXA ECONOMICA FEDERAL</option>
    <option value="033">BANCO SANTANDER BANESPA S.A.</option>
    <option value="399">HSBC BANK BRASIL S.A.</option>
    <option value="151">BANCO NOSSA CAIXA S.A.</option>
    <option value="745">BANCO CITIBANK S.A.</option>
    <option value="041">BANCO DO ESTADO DO RIO GRANDE DO SUL S.A.</option>
  </select>
 
  <input id="agency_number" placeholder="Agência" type="text"/>
  <input id="agency_check_number" placeholder="Dígito da agência" type="text" />
  <input id="account_number" placeholder="Conta corrente" type="text" />
  <input id="account_check_number" placeholder="Dígito da conta corrente" type="text" />
 
  <input type="button" value="Validar" id="validate_bank_account" />
</form>

<title>Projeto Volt - Juros bancários</title>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
		<script src="Chart.js" type="text/javascript"></script>
        <script src="Chart_1.js" type="text/javascript"></script>
        <script src="sheetsee.js" type="text/javascript"></script>
        <script src="tabletop1.3.4.js" type="text/javascript"></script>
        <script src= "jquery-1.11.3.min.js" type="text/javascript"></script>
        <script src="highlight.js" type="text/javascript"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" type="text/javascript"></script>
        
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
        <script src="js/bootstrap.min.js"></script>
        <link href='http://fonts.googleapis.com/css?family=Ubuntu' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" type="text/css" href="estilos.css">
        <link href='http://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700,900,400italic|Source+Code+Pro:400' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css">
        <link href="css/bootstrap.min.css" rel="stylesheet">
        
    </head>
	   <body>
           <div style="border-top: 0px #cbcbcb;width:50%;margin:0 auto;margin-bottom:50px;margin-top:20px; text-align:center;font-family:Ubuntu, Arvo, Georgia;">
           <a href="www.voltdata.info"><img alt="Logo Volt" style="width:60px;height:auto;border:0;" src="http://static1.squarespace.com/static/551da417e4b05f67005d6abe/t/551dadd4e4b095e92c168eba/1438001414943/?format=1500w"/></a> | Projetos Especiais 
                
           </div>
           
           
             <!--Tabela com todos os dados pesquisáveis-->
              
  <div class="container" style="">
    <h1>Quanto seu banco cobra de juros?</h1>
    <p>
    <input id="fullTableFilter" type="text" placeholder="Digite aqui o nome do seu banco cobra - Ex: Bradesco, Itaú (utilize acentos)"/>
    <div id="fullTable"></div> 

</div>

<script id="fullTable_template" type="text/html">
  <table>
    <th class="tHeader"></th><th class="tHeader">Cartão Rotativo <br>- ao mês (%)</th><th class="tHeader">Cartão Rotativo <br>- ao ano (%)</th> <th class="tHeader">Cheque Especial <br> - ao mês (%)</th><th class="tHeader">Cheque Especial <br> - ao ano (%)</th>
      {{#rows}}
        <tr style="text-align:center; border-right: 1px"><td>{{banco}}</td><td>{{cart1}}</td><td>{{cart2}}</td><td>{{chq1}}</td><td>{{chq2}}</td></tr>
      {{/rows}}
  </table>
</script>

<script type="text/javascript">
  document.addEventListener('DOMContentLoaded', function() {
    var URL = "https://docs.google.com/spreadsheets/d/1C0uC3hy4DsY56wHaUhlTdW0hy4rTm-1ZKcAj80iG-S4/pubhtml"
    Tabletop.init( { key: URL, callback: showInfo, simpleSheet: true } )
  })

  function showInfo(data) {
    var tableOptions = {"data": data
    , "pagination": 5, "tableDiv": "#fullTable", "filterDiv": "#fullTableFilter"}
    Sheetsee.makeTable(tableOptions)
    Sheetsee.initiateTableFilter(tableOptions)

    var html = Sheetsee.ich.photogrid({'rows': data})
    $('#photogrid').html(html)
  }

    
</script>
           <div id="credito" class="container">
           <h6>Compilado pelo Volt | Fonte: Banco Central</h6>
           </div>
           <br>
           <br>
           <br>
           <div id="texto" class="container">
               
               <p>
           Os juros mostrados acima são apenas uma referência de taxas cobradas pelo mercado para <strong>pessoas físicas</strong>, e dizem respeito a informações operações contratadas em julho de 2015, de acordo com dados do Banco Central do Brasil. 
           </p>
               <p>
            Taxas de juros variam entre tomadores de empréstimos, e os dados acima servem apenas como comparativo. Nem todos os bancos nem todas as taxas de juros foram mostrados aí. Porém, as maiores instituições bancárias do país estão nesse lista.
               </p>
               <p>
            Foram utilizados como referências as taxas de juros do rotativo do cartão e do cheque especial, que são taxas contratadas principalmente quando o cliente bancário está mais apertado financeiramente, e também estão entre as mais caras do mercado.   
               </p>
               <p>
            Você pode encontra todos os dados sobre juros cobrados por bancos <a href="http://www.bcb.gov.br/pt-br/sfn/infopban/txcred/txjuros/Paginas/default.aspx" target="_blank">neste link</a>, inclusive sobre crédito pessoal consignado e para pessoas jurídcas.
               </p>
           </div>
        <br>
           <br>
           <br>
           <br>
           <!--Calculadora de Juros-->
           
<div id="calculadora" class="container">
    <h1>Calculadora de Juros</h1>
           <form name="loandata">
  <table style="margin:0 auto;">
    <tr><td colspan="3"><strong></strong></td></tr>
    <tr>
      <td>Empréstimo ($):</td>
      <td><input type="text" name="principal" size="12" 
                 onchange="calculate();"></td>
    </tr>
    <tr>
      <td>Taxa de juros (mensal)</td>
      <td>
          <input type="text" name="interest" size="12" 
                 onchange="calculate();"></td>
    </tr>
    <tr>
      <td>Prazo (em meses):</td>
      <td><input type="text" name="years" size="12" 
                 onchange="calculate();"></td>
    </tr>
    <tr><td colspan="3">
      <input type="button" value="Calcular" onclick="calculate();">
    </td></tr>
    <tr><td colspan="3">
    </td></tr>
    <tr>
      <td><strong>Pagamento mensal:</strong></td>
      <td><input type="text" name="payment" size="12"></td>
    </tr>
    <tr>
      <td>Pagamento total:</td>
      <td><input type="text" name="total" size="12"></td>
    </tr>
    <tr>
      <td>Juros pagos:</td>
      <td><input type="text" name="totalinterest" size="12"></td>
    </tr>
  </table>
</form>
<script language="JavaScript">
function calculate() {
    var principal = document.loandata.principal.value;
    var interest = document.loandata.interest.value / 100 / 1;
    var payments = document.loandata.years.value * 1;

    var x = Math.pow(1 + interest, payments);
    var monthly = (principal*x*interest)/(x-1);

    if (!isNaN(monthly) && 
        (monthly != Number.POSITIVE_INFINITY) &&
        (monthly != Number.NEGATIVE_INFINITY)) {

        document.loandata.payment.value = round(monthly);
        document.loandata.total.value = round(monthly * payments);
        document.loandata.totalinterest.value = 
            round((monthly * payments) - principal);
    }
    // Otherwise, the user's input was probably invalid, so don't
    // display anything.
    else {
        document.loandata.payment.value = "";
        document.loandata.total.value = "";
        document.loandata.totalinterest.value = "";
    }
}

function round(x) {
  return Math.round(x*100)/100;
}
</script>
            </div>
           
           
           
           <!--Gráfico Cheque Especial-->
           
           <div class="grafico" id="graph1">
            <div class="grafico1">
               <h1>Juros cheque especial
		      </h1>
            <canvas id="especial" width="300" height="300"></canvas>
               </div>
               <!--Gráfico Cartão-->
             <div class="grafico2">
            <h1>Juros cartão - % ao ano
		      </h1>
            <canvas id="cartao" width="300" height="300"></canvas>
                 </div>
	   <script>
		var jurosespecial = 
            
            [
				{
					value: 195.03,
					color:"#F7464A",
					highlight: "#ededed",
					label: "Bradesco"
				},
				{
					value: 197.45,
					color: "#336699",
					highlight: "#ededed",
					label: "Caixa"
				},
				{
					value: 215.59,
					color: "#cdaf35",
					highlight: "#ededed",
					label: "Banco do Brasil"
				},
				{
					value: 247.26,
					color: "#cc8b2f",
					highlight: "#ededed",
					label: "Itaú"
				},
                {
					value: 305.93,
					color: "#443266",
					highlight: "#ededed",
					label: "Citibank"
				},
				{
					value: 348.56,
					color: "#FD2A19",
					highlight: "#ededed",
					label: "HSBC"
				},
                {
					value: 369.02,
					color: "#A6002E",
					highlight: "#ededed",
					label: "Santander"
				}
                
			];
           
           var juroscartao = 
            
            [			
				{
					value: 134.54,
					color: "#336699",
					highlight: "#ededed",
					label: "Caixa"
				},
				{
					value: 268.9,
					color: "#cdaf35",
					highlight: "#ededed",
					label: "Banco do Brasil"
				},
				{
					value: 430.06,
					color: "#443266",
					highlight: "#ededed",
					label: "Citibank"
				},
                {
					value: 433.08,
					color:"#F7464A",
					highlight: "#ededed",
					label: "Bradesco"
				},
				{
					value: 440.48,
					color: "#FD2A19",
					highlight: "#ededed",
					label: "HSBC"
				},
                {
					value: 495.57,
					color: "#A6002E",
					highlight: "#ededed",
					label: "Santander"
				},
                {
					value: 631.85,
					color: "#cc8b2f",
					highlight: "#ededed",
					label: "Itaú"
				}
                
			];
			window.onload = function(){
        var ctx1 = document.getElementById("especial").getContext("2d");
        var myPolarArea = new Chart(ctx1).PolarArea(jurosespecial, 
                {
					responsive:true,
                    animateScale: true,
                    segmentStrokeWidth : 5,
                    animationEasing : "southOutBounce",
                    showScale: true,
                    scaleLineWidth: 1,
                    scaleBeginAtZero: true,
                    scaleFontFamily: "'Monaco', 'Arvo', sans-serif",
                    scaleFontSize: 16,
                    tooltipFontFamily: "'Monaco', 'Arvo', sans-serif"
				});
        var ctx2 = document.getElementById("cartao").getContext("2d");
        var myPolarArea2 = new Chart(ctx2).PolarArea(juroscartao,
                {
					responsive:true,
                    animateScale: true,
                    segmentStrokeWidth : 5,
                    animationEasing : "southOutBounce",
                    showScale: true,
                    scaleLineWidth: 1,
                    scaleBeginAtZero: true,
                    scaleFontFamily: "'Monaco', 'Arvo', sans-serif",
                    scaleFontSize: 16,
                    tooltipFontFamily: "'Monaco', 'Arvo', sans-serif"
				});
                
                
};
	       </script>
           </div>
		
           <!--Mapa sobre juros no mundo-->
           
           <div class="container">
           <iframe width="100%" height="620" frameborder="0" seamless src="https://voltdatalab.cartodb.com/viz/3d1faf82-3663-11e5-a4e2-0e9d821ea90d/embed_map" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>
               </div>       
           
	</body>
</html>

</body>
</html>

<title>Calculadora Juros Compostos</title>
</head>

<body>
    <div class="container">
        <section class="content">
            <h3 class="text-center">Calculadora de Juros Compostos</h3>
            <hr>
            <form onsubmit="return false">
                <div class="row">
                    <div class="col-md-6">
                        <label class="control-label">Valor Inicial:</label>
                        <input class="montante form-control" type="number" placeholder="Valor inicial">
                    </div>
                    <div class="col-md-6">
                        <label class="control-label">Aporte Mensal:</label>
                        <input class="aporte form-control" type="number" placeholder="Senão, vazio">
                    </div>
                </div>
                <hr>
                <div class="row">
                    <legend>Taxa</legend>
                    <div class="col-md-6">
                        <label class="control-label">Mensal (padrão)</label>
                        <input class="taxa form-control" type="number" placeholder="Taxa de juros">
                    </div>
                    <div class="col-md-6">
                        <label class="control-label">Ou taxa anual</label>
                        <input class="taxaAno form-control" type="number" placeholder="Senão, vazio">
                    </div>
                </div>
                <hr>
                <div class="row">
                    <legend>Prazo</legend>
                    <div class="col-md-4">
                        <label class="control-label">Em meses (padrão)</label>
                        <input class="prazo form-control" type="number" placeholder="Meses">
                    </div>
                    <div class="col-md-4">
                        <label>Ou em anos</label>
                        <input class="prazoAno dataput form-control" type="number" placeholder="Senão, vazio">
                    </div>
                    <div class="col-md-4">
                        <label>Ou até data específica</label>
                        <input class="ateVencer dataput form-control" type="date" placeholder="Data do Vencimento">
                    </div>
                </div>
                <hr>
                <div class="row">
                    <div class="col-md-12 text-center">
                        <input type="submit" class="btn btn-primary btn-block btn-lg simulaUm" value="Calcular">
                    </div>
                </div>
            </form>
            <hr>
            <div class="row resultados">
                <div class="table-responsive">
                    <table class="table table-bordered table-hover table-striped table-dark">
                        <thead>
                            <tr>
                                <th>Aplicação inicial</th>
                                <th>Soma Aplicações</th>
                                <th>Juros totais</th>
                                <th>Acumulado</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>R$ <span class="apIn">.</span></td>
                                <td>R$ <span class="apOut">.</span></td>
                                <td>R$ <span class="apJu">.</span></td>
                                <td>R$ <span class="apTot">.</span></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <section>
                    <label class="control-label">Dados parciais e acumulados:</label>
                    <p></p>
                    <div id="printfinal" class="table-responsive">
                        <table class="table table-bordered table-hover table-striped table-dark">
                            <thead>
                                <tr>
                                    <th>Mês</th>
                                    <th>Aportes</th>
                                    <th>Juros no mês</th>
                                    <th>Juros total</th>
                                    <th>Acumulado</th>
                                </tr>
                            </thead>
                            <tbody></tbody>
                        </table>
                    </div>
                </section>
            </div>
        </section>
    </div>
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <script src="js/script.js"></script>

</body>

</html>






<div id="app"></div>
