---
layout: default
title: Drug Concentration Calculator
permalink: /tools/drugconcentration/
---

# Drug Concentration Calculator*

This calculator converts concentration between ng/mL and nM:

$$
nM = \frac{ng}{mL} * \frac{MW}{1000}
$$

<div id="calculator">
    <div>
        <label for="concentration">Concentration:</label>
        <div class="concentration-input-container">
            <input type="number" id="concentration" name="concentration" placeholder="[Concentration]">
            <div class="radio-group">
              <div class="radio-option">
                <input type="radio" id="nM" name="unit" value="nM" checked>
                nM
              </div>
              <div class="radio-option">
                <input type="radio" id="ngmL" name="unit" value="ngmL">
                ng/mL
              </div>
            </div>
        </div>
    </div>
    <div>
        <label for="mw">Molecular Weight:</label>
        <input type="number" id="mw" name="mw" placeholder="[g/mol]">
        g/mol
    </div>
    <div>
      <button id="calculate">Calculate</button>
      <button id="clear">Clear</button>
    </div>
    <div>
        <label for="result">Result:</label>
        <input type="text" id="result" name="result" readonly>
    </div>
</div>

<script>
    const calculateButton = document.getElementById('calculate');
    const clearButton = document.getElementById('clear');
    const concentrationInput = document.getElementById('concentration');
    const mwInput = document.getElementById('mw');
    const resultInput = document.getElementById('result');
    const radioButtons = document.querySelectorAll('input[name="unit"]');

    calculateButton.addEventListener('click', () => {
        const concentration = parseFloat(concentrationInput.value);
        const mw = parseFloat(mwInput.value);
        let currentUnit;
        for (const radioButton of radioButtons) {
            if (radioButton.checked) {
                currentUnit = radioButton.value;
                break;
            }
        }

        if (isNaN(concentration) || isNaN(mw)) {
            resultInput.value = "Invalid Input";
            return;
        }

        let result, resultUnit;
        if (currentUnit === 'nM') {
            result = (concentration * mw) / 1000;
            resultUnit = 'ng/mL';
        } else {
            result = (concentration * 1000) / mw;
            resultUnit = 'nM';
        }
        resultInput.value = `${result.toFixed(2)} ${resultUnit}`;
    });

    clearButton.addEventListener('click', () => {
        concentrationInput.value = "";
        mwInput.value = "";
        resultInput.value = "";
    })
</script>


*I made this calculator to practice using markdown, CSS, and scripting for the math.