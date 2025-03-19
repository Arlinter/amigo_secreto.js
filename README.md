# amigo_secreto.js
Sorteio de amigo secreto
function realizarSorteio(participantes) {
    let resultado = {};
    let disponiveis = [...participantes];

    participantes.forEach(participante => {
        let possibilidades = disponiveis.filter(nome => nome !== participante);

        if (possibilidades.length === 0) {
            throw new Error("Sorteio inválido. Tente novamente.");
        }

        let index = Math.floor(Math.random() * possibilidades.length);
        let escolhido = possibilidades[index];

        resultado[participante] = escolhido;
        disponiveis = disponiveis.filter(nome => nome !== escolhido);
    });

    return resultado;
}

// Lista de participantes
const participantes = ["Alice", "Bob", "Carol", "David"];

try {
    const sorteio = realizarSorteio(participantes);

    console.log("Resultado do sorteio de amigo secreto:");
    for (let [amigo, sorteado] of Object.entries(sorteio)) {
        console.log(`${amigo} tirou ${sorteado}`);
    }
} catch (erro) {
    console.error(erro.message);
}
