function verificarBandeira(numeroCartao) {
    const bandeiras = [
        { nome: "Visa", prefixos: ["4"], tamanho: [13, 16] },
        { nome: "MasterCard", prefixos: ["51", "52", "53", "54", "55", "2221", "2720"], tamanho: [16] },
        { nome: "American Express", prefixos: ["34", "37"], tamanho: [15] },
        { nome: "Elo", prefixos: ["401178", "438935", "451416", "5090", "6277", "6362"], tamanho: [16] },
        { nome: "Hipercard", prefixos: ["3841", "6062", "6370"], tamanho: [13, 16, 19] },
        { nome: "Diners Club", prefixos: ["300", "301", "302", "303", "304", "305", "36", "38"], tamanho: [14] },
        { nome: "Discover", prefixos: ["6011", "622126", "622925", "644", "645", "646", "647", "648", "649", "65"], tamanho: [16] },
        { nome: "Aura", prefixos: ["50"], tamanho: [16] },
    ];

    // Remove espaços ou traços do número do cartão
    const numeroLimpo = numeroCartao.replace(/[\s-]/g, "");

    for (const bandeira of bandeiras) {
        // Verifica se o tamanho do número é válido para a bandeira
        if (!bandeira.tamanho.includes(numeroLimpo.length)) {
            continue;
        }

        // Verifica se o prefixo do número corresponde a algum prefixo da bandeira
        for (const prefixo of bandeira.prefixos) {
            if (numeroLimpo.startsWith(prefixo)) {
                return bandeira.nome;
            }
        }
    }

    return "Bandeira desconhecida";
}

// Exemplo de uso
const numeroCartao = "4011 7812 3456 7890"; // Número de exemplo
const bandeira = verificarBandeira(numeroCartao);
console.log(`A bandeira do cartão é: ${bandeira}`);
