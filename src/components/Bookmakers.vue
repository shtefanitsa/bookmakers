
<template>
    <div class="hello">
        <h3> {{msg}} / {{ Bank + ' Zł' }} </h3>
        <div class="row">
        <table style="width:50%">
            <tr>
                <th>Teams</th>
                <th>Bank</th>
                <th>Odd</th>
                <th>Play</th>
                <th>Can Win</th>
            </tr>
            <tr>
                <td>{{TeamA}}</td>
                <td><input type="number" step="1" min="0" max="30" v-model.number="Match.TeamA[2]" v-on:input="$emit('BankA', $event.target.value)"></td>
                <td><input type="number" placeholder="1.0" step="0.01" min="1" max="40" v-model.number="Match.TeamA[1]" v-on:input="$emit('OddsA', $event.target.value)"></td>
                <td>{{PlayA + 'zł'}}</td> 
                <td>{{WinA + 'zł'}}</td> 
                <input type="text" >
            </tr>
            <tr>
                <td>{{TeamB}}</td>
                <td><input type="number" step="1" min="0" max="30" v-model.number="Match.TeamB[2]" v-on:input="$emit('BankB', $event.target.value)"></td>
                <td><input type="number" placeholder="1.0" step="0.01" min="1" max="40" v-model.number="Match.TeamB[1]" v-on:input="$emit('OddsB', $event.target.value)"></td>
                <td>{{PlayB + 'zł'}}</td> 
                <td>{{WinB + 'zł'}}</td> 
            </tr>
        </table>
       
     </div>
    <hr>
    </div>
    
</template>



<script>
export default {
    name: 'Bookmakers',
    props: {
        msg: String,
        TeamA: String,
        TeamB: String
    },
    data: function(){
    return {
        Draw: 0,
        Favorite: '',
        Match: {TeamA: ['',0,0],TeamB: ['',0,0],},
    }
    },
    computed: {

    PlayA: function () {
        const x = this.Match.TeamA[2] * 0.88
        return parseFloat(x.toFixed(2))
    },
    PlayB: function () {
        const x = this.Match.TeamB[2] * 0.88
        return parseFloat(x.toFixed(2))
    },
    WinA: function () {
        const x = this.Match.TeamA[1] * this.PlayA - this.Match.TeamA[2]
        return parseFloat(x.toFixed(2))
    },
    WinB: function () {
        const x = this.Match.TeamB[1] * this.PlayB - this.Match.TeamB[2]
        return parseFloat(x.toFixed(2))
    },
    Bank: function() {
        const x = this.Match.TeamB[2] + this.Match.TeamA[2]
        return x
    },
    method: {

    }
  }
}
</script>
<style>
* {
  box-sizing: border-box;
}

.row {
  display: flex;
}

/* Create two equal columns that sits next to each other */
#match {
  width: 50%;
  padding: 20px;
  height: 100px; /* Should be removed. Only for demonstration */
}
</style>