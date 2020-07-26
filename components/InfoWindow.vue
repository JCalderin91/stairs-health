<template>
    <div>
        <card/>
    </div>
</template>

<script>
import Card from '@/components/Card'
module.exports = {
    name: 'info-window',
    props: [ 
        'content',
    ],
    component: {Card}
}
</script>