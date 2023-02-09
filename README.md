# workerSearch


import {baseEnvData} from "../../config/_base";
import {urlEndpoints, workersItems, workersHeaders, itemNames, wrk1Worker} from "../../helper/names";
import {mainPage, workersFlow1} from "../../helper/selectors";
import {verifyTextOfEl} from "../../helper/asserts";
import {clearAndTypeText, clickOnEl, TypeText, clickOnElByText, inputText} from "../../helper/methods";
describe('Search worker', () => {

    beforeEach('Login', () => {
        cy.apiLogin(baseEnvData.businessOwner.email, baseEnvData.businessOwner.password);
        cy.visit(urlEndpoints.workersEndpoint);
    });

    it('Search for existing worker', () => {
        clickOnEl(workersFlow1.searchField)
        TypeText(workersFlow1.searchField, workersItems.wkr)
        verifyTextOfEl(workersFlow1.workerWholeField, workersItems.wkr)
        clickOnEl(workersFlow1.cleanWindowButton)
        clickOnEl(workersFlow1.searchField)
        // inputText(workersFlow1.searchField, workersItems.teamRoleWorker)
        // verifyTextOfEl(workersFlow1.workerWholeField, workersItems.teamRoleWorker)
        // inputText(workersFlow1.searchField, workersItems.nameWorker)
        // verifyTextOfEl(workersFlow1.workerWholeField, workersItems.nameWorker)
        // inputText(workersFlow1.searchField, workersItems.mobileNumberWorker)
        // verifyTextOfEl(workersFlow1.workerWholeField, workersItems.mobileNumberWorker)
        // inputText(workersFlow1.searchField, baseEnvData.businessOwner.email)
        // verifyTextOfEl(workersFlow1.workerWholeField, baseEnvData.businessOwner.email)
        // inputText(workersFlow1.searchField, workersItems.addressWorker)
        // verifyTextOfEl(workersFlow1.workerWholeField, workersItems.addressWorker)
    });


    it.only('Verify texts on the page', () => {
        cy.get(workersFlow1.workerWholeField).should('be.visible');
        wrk1Worker.forEach((el) =>
            cy.get(workersFlow1.workerWholeField).should('contain', `${el}`)
        );
    });
})
