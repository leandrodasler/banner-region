# banner-region

Essa funcionalidade foi implementada exclusivamente para demonstração e não foi testada em nenhuma loja em produção.

Requisitos iniciais de implementação:

Para contemplar a função de adicionar um banner com a possibilidade de ter uma exibição condicionada a franquia selecionada pelo cliente, será necessário a construção de uma app com os seguintes requisitos:


Builders:
- Store
- React

Fluxo:
A app deverá ter como dependência a app "store-image". Então, deverá ser construído um componente que encapsula a interface "list-context.image-list", alterando as propriedades do schema, e assim tornando possível inserir em qual franquia o slide devera aparecer.

Uma vez feito isso, filtrar as imagens do slide e exibir apenas as que estão definidas para a franquia selecionada. Então, será necessário exportar uma nova interface.

Script para pegar o nome da franquia selecionada:

fetch('/api/sessions', {
headers: { 'Content-Type': 'application/json' }, body: JSON.stringify({
public: { country: { value: 'BRA' }, postalCode: { value: "04538132" } },
}), method: 'POST', credentials: 'same-origin'
}).then(res => res.json()).then(res => {
const { regionId } = JSON.parse(atob(res.segmentToken));
const lojaFranquia = atob(regionId).slice(3);

console.log(lojaFranquia);
})
