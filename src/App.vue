<template>
    <div>
        <h1>Zapisy online na zajecia</h1>

        <div v-if="authenticatedUsername">
            <user-panel :username="authenticatedUsername" @logout="logMeOut()"></user-panel>
            <meetings-page></meetings-page>
        </div>

        <div v-else>
            <login-form @login="logMeIn($event)"></login-form>
        </div>
			<meetings-page v-show="authenticatedUserName" :user="authenticatedUserName"></meetings-page>
		
    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserPanel from "./UserPanel";
    import MeetingsPage from "./meetings/MeetingsPage";
    import NewMeetingForm from "./meetings/NewMeetingForm";
    import MeetingsList from "./meetings/MeetingsList";

    export default {
    	components: {LoginForm, MeetingsPage, UserPanel, NewMeetingForm, MeetingsList},
        data() {
            return {
                authenticatedUsername: '',
            }
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>
