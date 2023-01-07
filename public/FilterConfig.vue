<script lang="ts">

// @extraValue available if filterFunc.extra set to input
const filterFunc = (cellValue, extraValue) => {

   console.log("extravalye** " +extraValue + " cellvalue " + cellValue)
    if (!cellValue) {
        return false;
    }
    // if (typeof cellValue !== 'string') {
    //     cellValue = JSON.stringify(cellValue);
    // }
    return true;
};

filterFunc.extra = 'datepicker';

 export default function filterConfig() {
    return {
        customFilters: {
            include: ['newfilter'],
            'newfilter': {
                columnFilterType: 'myFilterType', // column filter type id
                name: 'Select range',
                func: filterFunc
            }
        },
        disableDynamicFiltering :false
    };
}



</script>

