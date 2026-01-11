async function translateText() {
    const inputText = document.getElementById('inputText').value.trim();
    const sourceLang = document.getElementById('source').value;
    const targetLang = document.getElementById('target').value;
    const outputText = document.getElementById('outputText');

    if (!inputText) {
        outputText.value = "Please enter text to translate.";
        return;
    }

    outputText.value = "Translating...";

    try {
        
        const proxyUrl = 'https://api.codetabs.com/v1/proxy?quest=';
        const googleUrl = `https://translate.googleapis.com/translate_a/single?client=gtx&sl=${sourceLang}&tl=${targetLang}&dt=t&q=${encodeURIComponent(inputText)}`;
        
        const response = await fetch(proxyUrl + encodeURIComponent(googleUrl));
        
        if (!response.ok) {
            throw new Error("Network error");
        }
        
        const data = await response.json();
        const translated = data[0][0][0]; 
        
        outputText.value = translated || "Translation unavailable.";
        
    } catch (error) {
        outputText.value = "Translation failed. Check connection.";
        console.error(error);
    }
}

function copyText() {
    const outputText = document.getElementById("outputText");

    if (!outputText.value) {
        alert("Nothing to copy");
        return;
    }

    outputText.select();
    outputText.setSelectionRange(0, 99999); // mobile support
    document.execCommand("copy");

    alert("Copied to clipboard!");
}




