# workerSearch

import {baseEnvData} from "../../config/_base";
import {urlEndpoints, workersItems, workersHeaders, itemNames, wrk1Worker} from "../../helper/names";
import {mainPage, workersFlow1} from "../../helper/selectors";
    import {verifyTextOfEl} from "../../helper/asserts";
    import {clearAndTypeText, clickOnEl, clickOnElByText, inputText, JustTypeText} from "../../helper/methods";

    describe('Search worker', () => {

beforeEach('Login', () => {
    cy.apiLogin(baseEnvData.businessOwner.email, baseEnvData.businessOwner.password);
    cy.visit(urlEndpoints.workersEndpoint);
});

it('Search for existing worker', () => {
    clickOnEl(workersFlow1.searchField)
    JustTypeText(workersFlow1.searchField, workersItems.wkr)
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


it('Verify texts on the page', () => {
            cy.get(workersFlow1.workerWholeField).should('be.visible');
            wrk1Worker.forEach((el) =>
                cy.get(workersFlow1.workerWholeField).should('contain', `${el}`)
            );
        });
    })



methods:

export const JustTypeText = (selector, text) => {
    cy.get(selector).should('be.visible').type(text);
}

names:

export const wrk1Worker = ['WKR-1', 'Vasya Pupkin', 'Serhiy Nehoda', 'Team Lead', '+1 (235) 345-4354', baseEnvData.businessOwner.email, '5435 Northwest 10th Court, Plantation, FL']


selectors:
export const workersFlow1 = {
    titleWorkers: '[data-qa="page-title"]',
    searchField: '[id="search-label"]',
    purchasedField: '[class="border-end pe-2 me-2"]',
    usedField: '[class="border-end pe-2"]',
    manageLicenses: '.MuiPaper-root',
    manageLicensesChild: '[class="MuiButtonBase-root MuiButton-root MuiButton-text MuiButton-textPrimary MuiButton-sizeMedium MuiButton-textSizeMedium css-c9cdx8-MuiButtonBase-root-MuiButton-root"]',
    manageWorkerLicenses: '[class="MuiTypography-root MuiTypography-h5 css-ag7rrr-MuiTypography-root"]',
    inviteWorker: '.MuiButton-outlinedPrimary',
    createWorkerButton: '[class="MuiButtonBase-root MuiButton-root MuiButton-contained MuiButton-containedPrimary MuiButton-sizeMedium MuiButton-containedSizeMedium MuiButton-root MuiButton-contained MuiButton-containedPrimary MuiButton-sizeMedium MuiButton-containedSizeMedium css-5b1qdu-MuiButtonBase-root-MuiButton-root"]',
    createWorkerNewWindow: '[class="MuiTypography-root MuiTypography-h5 css-ag7rrr-MuiTypography-root"]',
    table: '.regularTable',
    editWorker: '[data-testid="EditIcon"]',
    workerText: '[class="MuiGrid-root MuiGrid-item MuiGrid-grid-xs-12 MuiGrid-grid-md-6 MuiGrid-grid-lg-4 css-1e6jbaj-MuiGrid-root"]',
    workerField: 'tbody tr',
    workerWholeField: 'tbody tr',
    cleanWindowButton: '[data-testid="ClearIcon"]'
}

