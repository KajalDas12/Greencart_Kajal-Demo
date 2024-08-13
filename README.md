cddescribe('My First Test Suite',function() 
{

    it('My First Test Case',function() {

        // Visit the URL of the application
    cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
    cy.get('.search-keyword'). type('ca')
    cy.wait (2000)
    cy.get('.product').should('have.length',5)
    cy.get('.product:visible').should('have.length',4)
    //Parent child chaining
    cy.get('.products').find('.product').should('have.length', 4)
    cy.get('.products').find('.product').eq(2).contains('ADD TO CART').click()
    cy.get('.products').find('.product').each(($el, index, $list) => {

    const textveg = $el.find('h4.product-name').text()
     if(textveg.includes('Cashews'))
    {
     $el.find('button').click()
    }
})
 })
})
 it('should log the text of .brand element', () => {
  cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
  cy.get('.brand').then((logoelement) =>{
  
    const text = logoelement.text();
     
    cy.log(text);
  });
});

//-----------------

 describe('My Second Test Suite', function() 
{
 
it('My FirstTest case',function() {
 
 
cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/")
cy.get('.search-keyword').type('ca')
cy.wait(2000)
//selenium get hit url in browser, cypress get acts like findElement of selenium
 
//Parent child chaining
cy.get('.products').as('productLocator')
cy.get('@productLocator').find('.product').each(($el, index, $list) => {
 
const textVeg=$el.find('h4.product-name').text()
if(textVeg.includes('Cashews'))
{
$el.find('button').click()
}
})

cy.get('.cart-icon > img').click()
cy.contains('PROCEED TO CHECKOUT').click()
cy.contains('Place Order').click()

 