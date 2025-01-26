        //BOTTING MODULES
        initFolder({ location: tp.mainPanel, title: "Botting", storeAs: "bottingFolder", });
        initTabs({ location: tp.bottingFolder, storeAs: "bottingTab" }, [
            {
                title: "WIP", content:
`Sorry! No guide yet!
But check out the GitHub guide.`},
        ]);
            initModule({ location: tp.bottingTab.pages[0], title: "Show Panel", storeAs: "showBotPanel", tooltip: "Show the bot panel", bindLocation: tp.bottingTab.pages[1], button: "Show Panel", defaultBind: "J", clickFunction: () => {
                tp.botPanel.hidden = !tp.botPanel.hidden;
            }});
            tp.bottingTab.pages[0].addSeparator();
            initModule({ location: tp.bottingTab.pages[0], title: "How To?", storeAs: "bottingGuide", tooltip: "Click for infos on how to get started and free candy", button: "Link", clickFunction: function () { GM_openInTab(bottingGuideURL, { active: true }) }, });
        //THEMING MODULES
        initFolder({ location: tp.mainPanel, title: "Theming", storeAs: "themingFolder", });
        initTabs({ location: tp.themingFolder, storeAs: "themingTab" }, [
            {
                title: "WIP", content:
`Sorry! No guide yet!`},
        ]);
            initModule({ location: tp.themingTab.pages[0], title: "Skybox", storeAs: "skybox", tooltip: "Allows you to switch out Shell's default skybox", bindLocation: tp.themingTab.pages[1], dropdown: loadedSkyboxes, changeFunction: (newSkybox) => {
                if (!unsafeWindow[skyboxName]) return;
                unsafeWindow[skyboxName].material.reflectionTexture.coordinatesMode = L.BABYLON.Texture.SKYBOX_MODE;
            }});
            initModule({ location: tp.themingTab.pages[0], title: "Randomize Skybox", storeAs: "randomSkyBox", tooltip: "Switches the skybox to a random one", bindLocation: tp.themingTab.pages[1], });
            initModule({ location: tp.themingTab.pages[0], title: "Switch Interval", storeAs: "randomSkyBoxInterval", tooltip: "The interval after which the skybox is switched, given that randomSkyBox is enabled. In minutes", slider: { min: 1, max: 10, step: 0.1 }, defaultValue: 3, });
            tp.themingTab.pages[0].addSeparator();
            initModule({ location: tp.themingTab.pages[0], title: "Legacy Models", storeAs: "legacyModels", tooltip: "Switches to the old models", bindLocation: tp.themingTab.pages[1], });
            initModule({ location: tp.themingTab.pages[0], title: "Game Filter", storeAs: "filter", tooltip: "Adds a color tint to the game", bindLocation: tp.themingTab.pages[1], dropdown: [
                {text: "Default", value: 2},
                {text: "Blue", value: 3},
                {text: "Mexico", value: 4},
            ],});
            initModule({ location: tp.themingTab.pages[0], title: "Gun Position", storeAs: "gunPosition", tooltip: "Changes the position of your player's gun", bindLocation: tp.themingTab.pages[1], dropdown: [
                {text: "Right", value: "right"},
                {text: "Left", value: "left"},
                {text: "Hidden", value: "hidden"},
            ],});
            tp.themingTab.pages[0].addSeparator();
            initModule({ location: tp.themingTab.pages[0], title: "Enable Bob Modifier", storeAs: "bobModifierEnabled", tooltip: "Enable/disable setting the bob effect", bindLocation: tp.themingTab.pages[1], });
            initFolder({ location: tp.themingTab.pages[0], title: "Bob Modifier Settings", storeAs: "bobFolder", });
                initModule({ location: tp.bobFolder, title: "Bobbing Value", storeAs: "bobModifier", tooltip: "Set to 0 to disable. Mess with other numbers for funny effects.", slider: { min: 0, max: 99, step: 0.01 }, defaultValue: 0, });
                initModule({ location: tp.bobFolder, title: "Only When Still", storeAs: "bobModifierWhenStill", tooltip: "Disables while you're still.", bindLocation: tp.themingTab.pages[1], });
            tp.themingTab.pages[0].addSeparator();
            initFolder({ location: tp.themingTab.pages[0], title: "Audio Settings", storeAs: "audioFolder", });
                initModule({ location: tp.audioFolder, title: "Mute Game", storeAs: "muteGame", tooltip: "Mute the game?", bindLocation: tp.themingTab.pages[1], });
                initModule({ location: tp.audioFolder, title: "DistanMult", storeAs: "distanceMult", tooltip: "Makes the distance when playing sfx change", slider: { min: 0.01, max: 2, step: 0.01 }, defaultValue: 1, });
                tp.audioFolder.addSeparator();
                initModule({ location: tp.audioFolder, title: "CustomSFX (1st)", storeAs: "customSFX1", tooltip: "Select a custom sound pack. Changes in-game sounds. Three pack slots available at once", bindLocation: tp.themingTab.pages[1], enableConditions: [["muteGame", false]], dropdown: JSON.parse(JSON.stringify(retrievedSFX)), });
                initModule({ location: tp.audioFolder, title: "CustomSFX (2nd)", storeAs: "customSFX2", tooltip: "Select a custom sound pack. Changes in-game sounds. Three pack slots available at once", bindLocation: tp.themingTab.pages[1], enableConditions: [["muteGame", false]], dropdown: JSON.parse(JSON.stringify(retrievedSFX)), });
                initModule({ location: tp.audioFolder, title: "CustomSFX (3rd)", storeAs: "customSFX3", tooltip: "Select a custom sound pack. Changes in-game sounds. Three pack slots available at once", bindLocation: tp.themingTab.pages[1], enableConditions: [["muteGame", false]], dropdown: JSON.parse(JSON.stringify(retrievedSFX)), });
            tp.themingTab.pages[0].addSeparator();
            initModule({ location: tp.themingTab.pages[0], title: "Replace Logo", storeAs: "replaceLogo", tooltip: "Replaces shell shockers' BORING logo with the BEAUTIFUL StateFarm logo", bindLocation: tp.themingTab.pages[1], });
            initModule({ location: tp.themingTab.pages[0], title: "Animate Title", storeAs: "titleAnimation", tooltip: "Makes the page title look cool", bindLocation: tp.themingTab.pages[1], });
            initModule({ location: tp.themingTab.pages[0], title: "Client Theme", storeAs: "themeType", tooltip: "Controls the client's UI theme", bindLocation: tp.themingTab.pages[1], dropdown: [
                {text: "Default", value: "defaultTheme"},
                {text: "Iceberg", value: "icebergTheme"},
                {text: "Jet Black", value: "jetblackTheme"},
                {text: "Light", value: "lightTheme"},
                {text: "Retro", value: "retroTheme"},
                {text: "Translucent", value: "translucentTheme"},
                {text: "StateFarmer", value: "statefarmerTheme"},
                {text: "Blurple", value: "blurpleTheme"},
                {text: "ShellFarm", value: "shellFarmTheme"},
            ], defaultValue: "defaultTheme", changeFunction: function(value) {
                applyTheme(value.value);
            }});
            tp.themingTab.pages[0].addSeparator();
            initModule({ location: tp.themingTab.pages[0], title: "Enable Party Lights", storeAs: "partyLightsEnabled", tooltip: "🥳🥳 Let the party begin 🎉🎉", bindLocation: tp.themingTab.pages[1], });
            initModule({ location: tp.themingTab.pages[0], title: "Party Lights Intensity", storeAs: "partyLightsIntensity", tooltip: "Intensity of the party 🥳", slider: { min: 0.01, max: 20, step: 0.01 }, defaultValue: 0.5, });
            tp.themingTab.pages[0].addSeparator();
            initModule({ location: tp.themingTab.pages[0], title: "World Flattening", storeAs: "worldFlattening", tooltip: "Make the world F-L-A-T", slider: { min: 0.05, max: 10, step: 0.05 }, defaultValue: 1, });
            //ACCOUNT MODULES
        initFolder({ location: tp.mainPanel, title: "Accounts", storeAs: "accountsFolder", });
        initTabs({ location: tp.accountsFolder, storeAs: "accountsTab" }, [
            {
                title: "Basics", content:
`This is the accounts tab. Here you will find
options relating to managing your thousands of
shell accounts and options that will enable you
to alt like a pro.
 
NOTE: ShellPrint is currently unsupported on
this version of StateFarm Client.`},
            {
                title: "Login DB", content:
`The Login DB allows you to alt with ease. Put
simply, it is just a list of EmailPass combos.
It is simpler than AccountRecords, but one does
not replace the other. Login DB is stored
universally across all Shell proxies, and
has a queue system. Each time an account
from this list is logged into, it moves it
to the back of the list, allowing you to
have a steady stream of fresh accounts.
 
PRIVACY NOTE: This database will contain some
important information. All data is stored locally
and will never be requested by the StateFarm
development team, but can theoretically be stolen
via the use of other userscripts not authorised
by the StateFarm developers. This DB is not
exposed to the Shell Shockers game (unless you
have enabled debug mode).`},
            {
                title: "AccRecord", content:
`The AccountRecords database is similar, but
different to the Login DB. Whilst the Login DB
serves to allow you to quickly switch to a new
account, AccountRecords saves information
related to accounts you've logged into. It saves
info such as your egg count, items in your
inventory and the value of your inventory.
This feature is even more advanced than the
Login DB, and is only recommended for use by
people who really know what they're doing. If
you just like aimbotting, you really don't need
to worry about this.
 
FYI: This will attempt to save info about any
account, but will only perform best when you
are using an account that you logged into using
StateFarm's login or account creation modules.
Other accounts will have limited info, such as
masked emails and no EmailPass combos.
 
PRIVACY NOTE: This database will contain some
important information. You can disable the
logging of this info in the settings. All data
is stored locally and will never be requested
by the StateFarm development team, but can
theoretically be stolen via the use of other
userscripts not authorised by the StateFarm
developers. This DB is not exposed to the
Shell Shockers game (unless you have enabled
debug mode).`},
        ]);
            initFolder({ location: tp.accountsTab.pages[0], title: "Account Login (Basic)", storeAs: "loginFolder", });
                initModule({ location: tp.loginFolder, title: 'Email:Pass', storeAs: 'loginEmailPass', tooltip: "Field for loginLogin", defaultValue: "ex@gmail.com:passwd" });
                initModule({ location: tp.loginFolder, title: 'Login Account', storeAs: 'loginLogin', tooltip: "Log into an account using email:pass without using shell's UI", button: 'LOGIN', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let emailPass = extract("loginEmailPass");
                    if (emailPass.includes(":")) {
                        loginOrCreateWithEmailPass(emailPass);
                    } else {
                        emailPass = prompt('Your email:pass isn\'t valid. Enter your combo below or input the correct one in the box.', '');
                        if (emailPass.includes(":")) {
                            loginOrCreateWithEmailPass(emailPass);
                        }; //else fuck you. im not doing anything with that.
                    };
                } });
            tp.accountsTab.pages[0].addSeparator();
            initFolder({ location: tp.accountsTab.pages[0], title: "Account Login (Login Database)", storeAs: "loginDatabaseFolder", });
                initModule({ location: tp.loginDatabaseFolder, title: 'Login Next Account', storeAs: 'loginDatabaseLogin', button: 'LOGIN', tooltip: "Tools for managing accounts in a Database", bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let loginDB = GM_getValue("StateFarm_LoginDB") || []; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other. (yes this needed to be said again)
                    let loginDBlength = loginDB.length;
                    if (loginDBlength > 0) {
                        let index = extract("loginDatabaseSelection") == "inorder" ? 0 : Math.ceil((Math.random()*0.75)*(loginDBlength-1));
                        log(`selecting index ${index}, this is out of ${loginDBlength} entries.`);
                        let [emailPass] = loginDB.splice(index, 1); //delete and retrieve
                        loginDB.push(emailPass);
                        log(`deleted and reinserted ${emailPass} at the end.`);
                        loginOrCreateWithEmailPass(emailPass);
                        GM_setValue("StateFarm_LoginDB", loginDB);
                        createPopup(`Logging in from index ${index}...`);
                    } else {
                        createPopup("LoginDB is empty!", "error");
                    };
                } });
                initModule({ location: tp.loginDatabaseFolder, title: "Selection Type", storeAs: "loginDatabaseSelection", tooltip: "Tools for managing accounts in a Database", bindLocation: tp.accountsTab.pages[1], dropdown: [{ text: "In Order", value: "inorder" }, { text: "Random", value: "random" }], defaultValue: "inorder" });
                initModule({ location: tp.loginDatabaseFolder, title: "Auto Login", storeAs: "autoLogin", tooltip: "Tools for managing accounts in a Database", bindLocation: tp.accountsTab.pages[1], dropdown: [{ text: "Disabled", value: "disabled" }, { text: "When No Account", value: "noaccount" }, { text: "Always", value: "always" }], defaultValue: "disabled" });
                tp.loginDatabaseFolder.addSeparator();
                initModule({ location: tp.loginDatabaseFolder, title: 'Export DB(JSON)', storeAs: 'loginDatabaseExport', tooltip: "Tools for managing accounts in a Database", button: 'EXPORT (COPY)', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    GM_setClipboard(JSON.stringify(GM_getValue("StateFarm_LoginDB") || []), "text", () => log("Clipboard set!"));
                    createPopup("Login DB copied to clipboard...");
                } });
                initModule({ location: tp.loginDatabaseFolder, title: 'Import Into LoginDB', storeAs: 'loginDatabaseExport', tooltip: "Tools for managing accounts in a Database", button: 'APPEND (PASTE)', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let userInput = prompt(`Input data you would like to add to your LoginDB. This will NOT replace your current data. All data added here will be put at the end of the queue. Also make sure that this data goes here and not into the AccountRecords DB.`, 'Reminder: JSON format!');
                    try {
                        let loginDB = GM_getValue("StateFarm_LoginDB") || []; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other. (yes this needed to be said again)
                        let appendedData = JSON.parse(userInput);
                        appendedData.forEach(data => {
                            if (data && !loginDB.includes(data)) loginDB.push(data);
                        });
                        GM_setValue("StateFarm_LoginDB", loginDB);
                        createPopup("Success! Data appended to LoginDB.", "success");
                    } catch {
                        createPopup("Failed! Check the formatting.", "error");
                    };
                } });
                initModule({ location: tp.loginDatabaseFolder, title: 'ImportFromRecords', storeAs: 'loginDatabaseImportRecords', tooltip: "Tools for managing accounts in a Database", button: 'APPEND', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    if (prompt("This action will import any Email:Pass combos you have in AccountRecords. Make sure you want to do this, as this will potentially add a lot of new records. Type 'ok' to proceed. This cannot be reversed, export first to be safe. Note: all the new records are added to the end of the queue.") === 'ok') {
                        let accountRecords = GM_getValue("StateFarm_AccountRecords") || {}; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other.
                        let loginDB = GM_getValue("StateFarm_LoginDB") || []; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other. (yes this needed to be said again)
                        Object.entries(accountRecords).forEach(([key, account]) => {
                            let emailPass = account.emailPass;
                            if (emailPass && !loginDB.includes(emailPass)) {
                                loginDB.push(emailPass);
                            };
                        });
                        GM_setValue("StateFarm_LoginDB", loginDB);
                        createPopup("Appended from AccountDetails!", "success");
                    };
                } });
                initModule({ location: tp.loginDatabaseFolder, title: 'Delete LoginDB', storeAs: 'loginDatabaseDelete', tooltip: "Tools for managing accounts in a Database", button: 'DELETE!', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    if (prompt("WARNING! This is a destructive action! Type 'ok' if you are really sure you want to delete your LoginDB! This cannot be reversed, export first to be safe.") === 'ok') {
                        GM_setValue("StateFarm_LoginDB", []); //o7 data
                    };
                } });
                initModule({ location: tp.loginDatabaseFolder, title: 'LoginDB Info', storeAs: 'loginDatabaseInfo', tooltip: "Tools for managing accounts in a Database", button: 'INFO', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let loginDB = GM_getValue("StateFarm_LoginDB") || []; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other. (yes this needed to be said again)
                    alert(`You currently have ${loginDB.length} accounts in LoginDB. For info on what this is, check the guide tab.`);
                } });
            tp.accountsTab.pages[0].addSeparator();
            initFolder({ location: tp.accountsTab.pages[0], title: "Account Generator (Basic)", storeAs: "generatorFolder", });
                initModule({ location: tp.generatorFolder, title: 'Gmail (before @)', storeAs: 'accountGmail', tooltip: "The gmail prefix", defaultValue: "example (NO @gmail.com)" });
                initModule({ location: tp.generatorFolder, title: 'Password to use', storeAs: 'accountPass', tooltip: "The account's password", defaultValue: "password69" });
                initModule({ location: tp.generatorFolder, title: 'Create (Basic)', storeAs: 'accountCreate', tooltip: "Basic Gmail account creation", button: 'CREATE', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    loginOrCreateWithEmailPass(extract("accountGmail")+"+"+getScrambled()+"@gmail.com:"+extract("accountPass"));
                } });
            tp.accountsTab.pages[0].addSeparator();
            initFolder({ location: tp.accountsTab.pages[0], title: "Account Records Database", storeAs: "accountRecordsFolder", });
                initModule({ location: tp.accountRecordsFolder, title: "Disable Logging", storeAs: "accountRecordsLogging", tooltip: "Account Records Database options. Only needed when dealing with a lot of accounts", bindLocation: tp.accountsTab.pages[1], });
                initModule({ location: tp.accountRecordsFolder, title: 'Export DB (JSON)', storeAs: 'accountRecordsExport', tooltip: "Account Records Database options. Only needed when dealing with a lot of accounts", button: 'EXPORT (COPY)', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    GM_setClipboard(JSON.stringify(GM_getValue("StateFarm_AccountRecords") || {}), "text", () => log("Clipboard set!"));
                    createPopup("AccountRecords DB copied to clipboard...");
                } });
                initModule({ location: tp.accountRecordsFolder, title: 'Import Into DB', storeAs: 'accountRecordsImport', tooltip: "Account Records Database options. Only needed when dealing with a lot of accounts", button: 'APPEND (PASTE)', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let userInput = prompt(`Input data you would like to add to your AccountRecords DB. This will NOT replace your current data. All data added here either be added or replace existing records. Also make sure that this data goes here and not into the LoginDB.`, 'Reminder: JSON format!');
                    try {
                        let accountRecords = GM_getValue("StateFarm_AccountRecords") || {}; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other.
                        let appendedData = JSON.parse(userInput);
                        Object.entries(appendedData).forEach(([key, account]) => {
                            if (account) accountRecords[key] = account;
                        });
                        GM_setValue("StateFarm_AccountRecords", accountRecords);
                        createPopup("Success! Data appended to AccountRecords.", "success");
                    } catch {
                        createPopup("Failed! Check the formatting.", "error");
                    };
                } });
                initModule({ location: tp.accountRecordsFolder, title: 'Delete DB', storeAs: 'accountRecordsDelete', tooltip: "Account Records Database options. Only needed when dealing with a lot of accounts", button: 'DELETE!', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    if (prompt("WARNING! This is a destructive action! Type 'ok' if you are really sure you want to delete your AccountRecords DB! This cannot be reversed, export first to be safe.") === 'ok') {
                        GM_setValue("StateFarm_AccountRecords", {}); //o7 data
                    };
                } });
                initModule({ location: tp.accountRecordsFolder, title: 'View Info', storeAs: 'accountRecordsInfo', tooltip: "Account Records Database options. Only needed when dealing with a lot of accounts", button: 'INFO', bindLocation: tp.accountsTab.pages[1], clickFunction: function () {
                    let userInput = prompt(`This will output some information relating to what information you have in your AccountRecords DB.\nParameters: Enter 1 to only print Email:Pass list of those with items, enter 2 for those with no items.`, '');
                    let accountRecords = GM_getValue("StateFarm_AccountRecords") || {}; //why declare this so many times? the DBs need to be constantly rechecked, as other clients may have modified. we wouldnt want to be overwriting each other.
                    let tierCache = GM_getValue("StateFarm_TierCache") || {};
                    const itemCounts = {};
                    const tierCounts = {};
                    let emailPassList = [];
                    let accountCount = 0;
                    let accountWithItemsCount = 0;
                    let itemCountTotal = 0;
                    Object.entries(accountRecords).forEach(([key, account]) => {
                        if (account) {
                            let countedAccount = false; accountCount++;
                            let inventoryList=[];
                            account.inventory.forEach(item=>{inventoryList.push(item.name)});
                            if (inventoryList) {
                                for (let item of inventoryList) {
                                    if (!countedAccount) {countedAccount = true; accountWithItemsCount++};
                                    if (tierCache[item]) {
                                        item = `${item} [T${tierCache[item]}]`;
                                    };
                                    let tier = item.match(/\[T([0-9])\]/);
                                    if (tier && tier[1]) {
                                        if (tierCounts.hasOwnProperty(tier[1])) {
                                            tierCounts[tier[1]]++;
                                        } else {
                                            tierCounts[tier[1]] = 1;
                                        };
                                    };
                                    itemCountTotal++;
                                    if (itemCounts.hasOwnProperty(item)) {
                                        itemCounts[item]++;
                                    } else {
                                        itemCounts[item] = 1;
                                    };
                                };
                                if (account.emailPass && !emailPassList.includes(account.emailPass)) {
                                    if ((userInput == "1" && inventoryList.length > 0) || // with items
                                        (userInput == "2" && inventoryList.length < 1) || // no items
                                        (userInput !== "1" && userInput !== "2")) { // do them all
                                        emailPassList.push(account.emailPass);
                                    };
                                };
                            };
                        };
                    });
                    log('%c' + ' '.repeat(500), 'background: white; color: white; font-size: 50px;');
                    log('%cAccountRecords Info', 'color: red; font-size: 30px;');
                    log("Full AccountRecords:");
                    log(accountRecords);
                    log(`itemCounts (Total items: ${itemCountTotal}):`);
                    log(itemCounts);
                    log(`tierCounts:`);
                    log(tierCounts);
                    log(`tierCache:`);
                    log(tierCache);
                    log(`emailPassList (Count: ${emailPassList.length}):`);
                    log(JSON.stringify(emailPassList));
                    log('%c' + ' '.repeat(500), 'background: white; color: white; font-size: 50px;');
                    alert(`Results:\nAccounts Total: ${accountCount}; With Items: ${accountWithItemsCount}\nItem Count: ${itemCountTotal}\nOther info has been pasted into console.`);
                } });
            tp.accountsTab.pages[0].addSeparator();
            initFolder({ location: tp.accountsTab.pages[0], title: "Account Generator (ShellPrint)", storeAs: "shellPrintFolder", });
            initModule({ location: tp.shellPrintFolder, title: 'ShellPrint Key', storeAs: 'shellPrintKey', tooltip: "ShellPrint token. NOTE: ShellPrint is currently unsupported on this version of StateFarm Client", defaultValue: "" });
            initModule({ location: tp.shellPrintFolder, title: ' ', storeAs: 'getSPKey', tooltip: "ShellPrint help. NOTE: ShellPrint is currently unsupported on this version of StateFarm Client", button: 'Get a Key', clickFunction: () => GM_openInTab(discordURL, { active: true }) });
            initModule({ location: tp.shellPrintFolder, title: 'Create (ShellPrint)', storeAs: 'shellprintGen', tooltip: "Account creation using ShellPrint™ technology. NOTE: ShellPrint is currently unsupported on this version of StateFarm Client", button: 'Generate!', clickFunction: () => F.register(), bindLocation: tp.accountsTab.pages[1] });
            tp.accountsTab.pages[0].addSeparator();
        //MISC MODULES
        initFolder({ location: tp.mainPanel, title: "Misc", storeAs: "miscFolder", });
        initTabs({ location: tp.miscFolder, storeAs: "miscTab" }, [
            {
                title: "WIP", content:
`Sorry! No guide yet!`},
        ]);
            //move this stuff to top bc its more important
            initFolder({ location: tp.miscTab.pages[0], title: "Ban Evasion Options", storeAs: "banFolder", });
                initModule({ location: tp.banFolder, title: "Unban", storeAs: "unban", tooltip: "Unbans you by signing out. You will lose skins if you're not signed in.", bindLocation: tp.miscTab.pages[1], button: "UNBAN NOW", clickFunction: function(){
                    if (GM_getValue('StateFarm_Unbanned')) unban();
                    else if (prompt("By proceeding, you will be signed out. If you don't have an account, your stats will be lost.\nEnter 'ok' to confirm this.\nThis popup will not be shown again for future unbans.") === 'ok') {
                        GM_setValue('StateFarm_Unbanned', 'true');
                        unban();
                    } else {
                        alert('You did not entire "ok", so the unban was cancelled.');
                    };
                },});
                initModule({ location: tp.banFolder, title: "Auto Unban", storeAs: "autoUnban", tooltip: "Automatically detects bans & unbans in above fashion", bindLocation: tp.miscTab.pages[1],});
                initModule({ location: tp.banFolder, title: "New Proxy", storeAs: "newProxy", tooltip: "Switches to a new shell shockers link. SF config won't be transferred", bindLocation: tp.miscTab.pages[1], button: "NEW PROXY", clickFunction: function(){
                    const userConfirmed=confirm("Switching to a proxy URL. By proceeding, you will enter another URL for Shell Shockers but your data doesn't get transferred.");
                    if (userConfirmed) {
                        newProxy();
                    };
                },});
                initModule({ location: tp.banFolder, title: "Reload Page", storeAs: "reload", tooltip: "Reloads the page", bindLocation: tp.miscTab.pages[1], button: "RELOAD NOW", clickFunction: function(){
                    reloadPage();
                },});
            tp.miscTab.pages[0].addSeparator();
            initFolder({ location: tp.miscTab.pages[0], title: "Ad & Privacy Options", storeAs: "adFolder", });
                initModule({ location: tp.adFolder, title: "Ad Block", storeAs: "adBlock", tooltip: "Prevents the anti-adblocker code. NOTE: this will always display the VIP badge as a side effect", bindLocation: tp.miscTab.pages[1], });
                initModule({ location: tp.adFolder, title: "VIP Spoof", storeAs: "spoofVIP", tooltip: "Makes the VIP badge visible locally (other players won't see)", bindLocation: tp.miscTab.pages[1], });
                initModule({ location: tp.adFolder, title: "NoAnnoyances", storeAs: "noAnnoyances", tooltip: "Removes ads", bindLocation: tp.miscTab.pages[1], });
                initModule({ location: tp.adFolder, title: "NoTrack", storeAs: "noTrack", tooltip: "Removes some user data tracking code", bindLocation: tp.miscTab.pages[1], });
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "AntiAFK", storeAs: "antiAFK", tooltip: "Bypasses AFK kicks", bindLocation: tp.miscTab.pages[1], });
            initModule({ location: tp.miscTab.pages[0], title: "Quick Respawn", storeAs: "quickRespawn", tooltip: "Respawns quicker than usual", bindLocation: tp.miscTab.pages[1], });
            initModule({ location: tp.miscTab.pages[0], title: "Sneaky Despawn", storeAs: "sneakyDespawn", tooltip: "Despawns, similar to the Esc key, but you can move while despawning, not that you cannot deal damage while sneaky despawning", bindLocation: tp.miscTab.pages[1], button: "Despawn... soon!", defaultBind: "Backquote", clickFunction: function(){
                if (!(unsafeWindow.extern.gamePaused || sneakyDespawning)) {
                    sneakyDespawning = true;
                    ss.PAUSE(); createPopup("SneakyDespawn: 3 seconds.");
                    setTimeout(() => { createPopup("SneakyDespawn: 2 seconds.");
                    }, 1e3);
                    setTimeout(() => { createPopup("SneakyDespawn: 1 second.");
                    }, 2e3);
                    setTimeout(() => { createPopup("SneakyDespawn: Now despawning!");
                        document.exitPointerLock(); document.onpointerlockchange();
                        setTimeout(() => {
                            sneakyDespawning = false;
                        }, 200);
                    }, 3e3);
                };
            },});
            tp.miscTab.pages[0].addSeparator();
            initFolder({ location: tp.miscTab.pages[0], title: "StateFarm UI Options", storeAs: "sfcUIFolder", });
                initModule({ location: tp.sfcUIFolder, title: "StateFarm Updates", storeAs: "statefarmUpdates", tooltip: "Shows a element at the home screen about statefarm's update history, notifies you when update is available", bindLocation: tp.miscTab.pages[1], defaultValue: true, });
                initModule({ location: tp.sfcUIFolder, title: "Replace Feeds", storeAs: "replaceFeeds", tooltip: "Replaces the game menu's news and videos feed with content by the StateFarm dev team", bindLocation: tp.miscTab.pages[1], defaultValue: true, });
                initModule({ location: tp.sfcUIFolder, title: "Custom Badges", storeAs: "customBadges", tooltip: "Enables custom StateFarm badges", bindLocation: tp.miscTab.pages[1], defaultValue: true, });
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "Unlock Skins (View Only)", storeAs: "unlockSkins", tooltip: "Unlocks all skins in locally (other players will not see these)", bindLocation: tp.miscTab.pages[1], });
            initModule({ location: tp.miscTab.pages[0], title: "Unlock Bros Grenade", storeAs: "brosGrenade", tooltip: "Unlocks the real bros grenade skin to your account", bindLocation: tp.miscTab.pages[1], button: "Unlock, real.", clickFunction: function(){
                extern.giveBasketBrosReward();
            },});
            initModule({ location: tp.miscTab.pages[0], title: "Admin Spoof", storeAs: "adminSpoof", tooltip: "Shows admin options such as BOOT and BAN in games. No ACTUAL functionality", bindLocation: tp.miscTab.pages[1], });
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "Switch Focus", storeAs: "unfocus", tooltip: "Controls the focus of the game. Allows for tabbing out without despawning", bindLocation: tp.miscTab.pages[1], button: "FOCUS/UNFOCUS", defaultBind: "P", clickFunction: function(){
                if (document.pointerLockElement !== null) { //currently locked
                    noPointerPause=true; unsafeWindow.document.exitPointerLock();
                } else if (noPointerPause) { //already unlocked?
                    noPointerPause=false;
                    unsafeWindow.canvas.requestPointerLock();
                };
            },});
            tp.miscTab.pages[0].addSeparator();
            initFolder({ location: tp.miscTab.pages[0], title: "Chicken Winner Options", storeAs: "chwFolder", });
                initModule({ location: tp.chwFolder, title: "FastChickenWinner", storeAs: "chickenWinner", tooltip: "Instantly plays the chick'n winner minigame", bindLocation: tp.miscTab.pages[1], button: "Force Play", clickFunction: function(){
                    unsafeWindow.extern.chwTryPlay();
                    const eggElement = document.getElementById("eggOne");
                    eggElement.click();eggElement.click();eggElement.click();eggElement.click();eggElement.click();eggElement.click();eggElement.click();eggElement.click();eggElement.click();
                    let chicknWinnerElementLoaded = false;
                    const checkInterval = setInterval(() => {
                        const chicknWinnerElement = document.getElementById('chicknWinner');
                        chicknWinnerElementLoaded = (chicknWinnerElement?.style?.display == ''); //idk, this is kind of shit? but who actually cares that much...
                        if (chicknWinnerElementLoaded) {
                            const gotWinnerOkElement = document.getElementById('gotWinnerOk');
                            if (gotWinnerOkElement) {
                                gotWinnerOkElement.click();
                            };
                            if (chicknWinnerElement.style.display == 'none') {
                                log("ermm, found");
                                clearInterval(checkInterval);
                                updateAccountRecords();
                                accountStatus = "chwDone";
                            };
                        };
                    }, 100);
                },});
                initModule({ location: tp.chwFolder, title: "AutoChickenWinner", storeAs: "autoChickenWinner", tooltip: "Automatically plays the chick'n winner minigame when cooldowns are over", bindLocation: tp.miscTab.pages[1],});
                initModule({ location: tp.chwFolder, title: "Chw Info Notifications", storeAs: "chickenWinnerNotifs", tooltip: "Alerts you of the tier of what you just earned and other infos.", bindLocation: tp.miscTab.pages[1],});
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "Get Game History", storeAs: "getGameHistory", tooltip: "Displays a list of the last few lobbies you were in", bindLocation: tp.miscTab.pages[1], button: "get", clickFunction: function(){
              let games = GM_getValue("StateFarm_GameHistory");
              //alert(GM_getValue("StateFarm_GameHistory"));
              if(!games) {
              alert("no history!");
                return;
              }
              games = JSON.parse(games);
              let gString = "";
              games.forEach(g => {
                gString+= g.code;
                if(g.amount>1) gString += ` (${g.amount})`;
                gString+= ": ";
                gString+= g.string; //omggggg
 
                gString+= ` (left at ${new Date(g.time).toLocaleString()} via ${g.closeCode} ${g.message})`
 
                gString += "\n";
              });
              console.log(gString); //debated using log(), but this is a direct user input so yhhhhhhhh
              gString+="\na copy of this list has been dumped into the console, if you wish to copy a code.";
              alert(gString);
            },});
            initModule({ location: tp.miscTab.pages[0], title: "Clear Game History", storeAs: "clearGameHistory", tooltip: "Clear your stored game history", bindLocation: tp.miscTab.pages[1], button: "clear", clickFunction: function(){
              if(!GM_getValue("StateFarm_GameHistory")) return;
              log("deleting game history: " + GM_getValue("StateFarm_GameHistory"));
              GM_deleteValue("StateFarm_GameHistory");
              createPopup("game history deleted!");
            },});
            initModule({ location: tp.miscTab.pages[0], title: "Custom Macro", storeAs: "customMacro", tooltip: "The JavaScript macro executed via executeMacro", defaultValue: "log('cool');" });
            initModule({ location: tp.miscTab.pages[0], title: "Execute Macro", storeAs: "executeMacro", tooltip: "Allows for JS code to be executed from the client itself. Runs in userscript environment, so use unsafeWindow etc.", bindLocation: tp.miscTab.pages[1], button: "EXECUTE", clickFunction: function(){
                //use at your own risk, i guess. but is this really any more dangerous than pasting something into console? not really.
                (async () => {
                    try {
                        log(extract("customMacro"));
                        // stay safe out there. this runs in the **userscript** environment. make sure to use unsafeWindow for whatever reason you may need the window object.
                        await eval(extract("customMacro")); // eslint-disable-line
                    } catch (error) {
                        console.error("Error executing code:", error);
                    }
                })();
            },}); //but yes, as you can see "macros" are just scripts you can execute for whatever purposes you need. reminds me of userscripts...
            initModule({ location: tp.miscTab.pages[0], title: "Do At Startup", storeAs: "autoMacro", tooltip: "Executes the entered macro at client startup", bindLocation: tp.miscTab.pages[1],});
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "[WIP]RandomPath", storeAs: "randomPath", tooltip: "Forces a new random path (pathfinding currently disabled)", bindLocation: tp.miscTab.pages[1], button: "Random Path", clickFunction: function(){
                findNewPath = true;
            },});
            findNewPath = false;
            tp.miscTab.pages[0].addSeparator();
            initModule({ location: tp.miscTab.pages[0], title: "SilentRoll", storeAs: "silentRoll", tooltip: "Rolls around without showing it client sided", bindLocation: tp.miscTab.pages[1], });
            initFolder({ location: tp.miscTab.pages[0], title: "Seizure Options", storeAs: "seizureFolder", });
                initModule({ location: tp.seizureFolder, title: "SeizureX", storeAs: "enableSeizureX", tooltip: "Rotates the player by the specified amount around the y-axis (yaw)", bindLocation: tp.miscTab.pages[1], });
                initModule({ location: tp.seizureFolder, title: "X Amount", storeAs: "amountSeizureX", tooltip: "Amount to roll", slider: { min: -6.283185307179586, max: 6.283185307179586, step: Math.PI / 280 }, defaultValue: 2, });
                initModule({ location: tp.seizureFolder, title: "SeizureY", storeAs: "enableSeizureY", tooltip: "Rotates the player by the specified amount around the x-axis (pitch)", bindLocation: tp.miscTab.pages[1], });
                initModule({ location: tp.seizureFolder, title: "Y Amount", storeAs: "amountSeizureY", tooltip: "Amount to roll", slider: { min: -6.283185307179586, max: 6.283185307179586, step: Math.PI / 280 }, defaultValue: 2, });
