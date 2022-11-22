


const initialWagonState = {
  supplies: 100,
  distance: 0,
  days: 0,
}

console.log(initialWagonState )
const callReducer = (state = initialWagonState, action) => {
 switch(action.type) {
   case 'gather': {
     return {
      ...state,
      supplies: state.supplies + 15,
      distance: state.distance,
      days: state.days + 1
     }
   }
   case 'travel': {
     return {
      ...state,
      supplies: state.supplies - (20 * 3),
      distance: state.distance + (10 * 3),
      days: state.days + 3
     }
   }
   case 'tippedWagon': {
     return {
      ...state,
      supplies: state.supplies - 30,
      distance: state.distance,
      days: state.days + 1
     }
   }
   default: {
     return state
   }
 } 
 
}

let wagon = callReducer(undefined, {});
console.log('initial state')
console.log(wagon);

wagon = callReducer(wagon, {type: 'travel', payload: 1})
console.log(wagon);

wagon = callReducer(wagon, {type: 'gather', payload: 0})
console.log(wagon);

wagon =  callReducer(wagon, {type: 'tippedWagon', payload: 0})
console.log(wagon);

wagon = callReducer(wagon, {type: 'travel', payload: 3})
console.log(wagon)




Output:
{ supplies: 100, distance: 0, days: 0 }
initial state
{ supplies: 100, distance: 0, days: 0 }
{ supplies: 40, distance: 30, days: 3 }
{ supplies: 55, distance: 30, days: 4 }
{ supplies: 25, distance: 30, days: 5 }
{ supplies: -35, distance: 60, days: 8 }